# Architecture 

This page describes the runtime architecture of MEMS. It focuses on the services that make up the system, how they interact, and how MEMS depends on VC Hub.

## Overview

MEMS is a containerized system composed of an application service, an identity service, dedicated data stores, a reverse proxy, and an observability stack. It integrates with VC Hub as an external platform for identity brokering and operational connectivity.

```text
Client browser
    |
    | HTTPS
    v
nginx reverse proxy
    |
    +--> MEMS application
    |       |
    |       +--> MEMS PostgreSQL database
    |       |
    |       +--> Keycloak
    |       |
    |       +--> VC Hub
    |
    +--> Keycloak
    |
    +--> Grafana

Observability path:
MEMS application --> OpenTelemetry Collector --> Loki / Tempo / Prometheus --> Grafana
```

All user-facing access is routed through nginx. Internal services communicate over the private container network.

## Service Landscape

| Service | Purpose |
| --- | --- |
| nginx reverse proxy | Terminates TLS and exposes the public HTTPS endpoints for MEMS, Keycloak, and Grafana |
| MEMS application | Hosts the MEMS web UI, backend API, and the business logic for monitoring and control |
| Keycloak | Provides authentication and identity brokering |
| PostgreSQL for MEMS | Stores MEMS application data and history data |
| PostgreSQL for Keycloak | Stores Keycloak realm, client, and identity configuration |
| OpenTelemetry Collector | Receives telemetry from MEMS and forwards it to the monitoring backends |
| Loki | Stores application and platform logs |
| Tempo | Stores distributed traces |
| Prometheus | Stores metrics and scrape results |
| Grafana | Provides dashboards for metrics, logs, traces, and operational visibility |
| blackbox-exporter | Probes service endpoints and exposes probe metrics |
| VC Hub | External dependency that provides the upstream integration endpoint and identity relationship for MEMS |

## Network and Access Model

nginx acts as the single public HTTPS entry point. It receives browser traffic and forwards requests to the relevant internal service. This keeps the internal services behind a single TLS termination layer and a shared network boundary.

| Endpoint | Default port | Notes |
| --- | --- | --- |
| MEMS | 9443 | Main user entry point |
| Keycloak | 8443 | Browser redirects go here for login |
| Grafana | 3443 | Operational dashboards |
| Keycloak PostgreSQL | 5433 | Administrative or maintenance access only |
| MEMS PostgreSQL | 5434 | Administrative or maintenance access only |

Loki, Tempo, Prometheus, the OpenTelemetry Collector, and blackbox-exporter are internal services. They are intended to communicate inside the service network rather than serve end users directly.

## Core Runtime Flow

### 1. User access

Users open the MEMS URL over HTTPS. nginx terminates TLS and forwards requests to the MEMS application.

### 2. Authentication

When authentication is required, the browser is redirected to Keycloak. Keycloak brokers identity with VC Hub and returns the authenticated user session to MEMS.

### 3. Application processing

The MEMS application handles the web UI, API requests, and the application logic for microgrid monitoring and control. It stores operational and historical data in the MEMS PostgreSQL database.

### 4. External integration

VC Hub is an external system that MEMS depends on. It provides the integration point outside the MEMS runtime boundary and is reached over its configured HTTPS endpoint.

### 5. Observability

The MEMS application emits telemetry to the OpenTelemetry Collector. Logs, traces, and metrics are then stored in Loki, Tempo, and Prometheus and explored through Grafana dashboards.

## Certificates and Trust

nginx presents the server certificate to clients and forwards traffic to the internal services.

Trust is handled in three places:

- Browsers must trust the certificate served by nginx.
- Keycloak must trust the endpoints it calls, when private or self-signed CAs are used.
- MEMS must trust VC Hub and Keycloak, when private or self-signed CAs are used.

## Data and Persistence

The MEMS runtime persists application, identity, and observability data in dedicated storage areas rather than inside ephemeral containers.

- MEMS PostgreSQL stores application and history data.
- Keycloak PostgreSQL stores identity and realm configuration.
- Loki, Tempo, and Prometheus store observability data for later inspection.

This separation keeps service state durable across container restarts.

## Architecture Boundaries

The MEMS runtime boundary includes the reverse proxy, the application, the identity service, the databases, and the observability services. VC Hub sits outside that boundary as an external system dependency.

Within that boundary:

- MEMS owns its application processing and local service-to-service communication.
- Keycloak owns authentication inside the MEMS landscape.
- VC Hub remains responsible for the external platform capabilities it exposes to MEMS.
- Grafana provides an operator view into observability data generated within the MEMS landscape.

## Summary

MEMS is a service-based runtime centered on the MEMS application, fronted by nginx, secured through Keycloak, backed by dedicated PostgreSQL databases, and observed through the OpenTelemetry, Loki, Tempo, Prometheus, and Grafana toolchain. VC Hub is the primary external dependency and forms the key integration boundary outside the MEMS runtime itself.