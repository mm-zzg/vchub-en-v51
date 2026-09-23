# Main Functions

MEMS is the supervisory layer that turns a collection of local power assets into a coordinated microgrid. It monitors the real-time state of generation, storage, consumption, and grid exchange, then applies control logic to keep the system safe, stable, and efficient. In practice, MEMS is responsible for the decisions that connect individual devices into one operating energy system.

The functional scope of MEMS is aligned with the current product requirements: it supports grid-connected microgrid operation, manages distributed energy resources, optimizes storage use, and provides visibility for operators and engineers.

## Functional Overview

MEMS covers the main operational functions required to run a modern microgrid in a controlled and repeatable way:

- real-time monitoring of the complete energy system
- coordination of generation, storage, loads, and grid power exchange
- peakload  management and surplus management
- alarm handling and operational status monitoring
- reporting for energy consumption 

## 1. Real-Time Monitoring and System State Awareness

MEMS continuously collects and interprets data from the microgrid. This includes power flows, voltages, currents, battery state of charge, generator status, load demand, and grid conditions. By consolidating these values in one supervisory layer, MEMS gives operators a clear operational picture of the current energy state.

Typical monitoring functions include:

- live view of generation from PV or other generators, and grid import/export
- battery state of charge, charging limits, and discharge limits
- energy exchange with the public grid or upstream network

This visibility is essential for both daily operation and incident response. Without a unified state model, operators would have to interpret each device separately, which makes safe and efficient control much harder.


## 2. Battery Energy Management and Storage Optimization

Battery storage is one of the most important assets in a microgrid because it provides flexibility, reserve capacity, and dynamic balancing. MEMS manages storage according to operating constraints and strategic goals.

Core functions include:

- charge and discharge control based on current demand and generation surplus
- enforcement of charging restrictions and time-based charging schedules
- prioritization of battery use for peak reduction, renewable shifting, and other operational objectives

This allows the microgrid to absorb surplus renewable energy, release stored energy during shortages, and reduce peak grid demand without overstressing the battery system.

## 3. Peak Load Management and Reactivation

One of the key industrial objectives in microgrid operation is to avoid unnecessary power peaks. MEMS includes a coordinated Peak Load Management and Reactivation strategy that monitors the combined demand and takes corrective action before a limit is exceeded.

Typical peak management behavior includes:

- discharge battery storages
- decrease consumption of controllable consumers
- turn off binary controlled consumer

When the peak condition is relieved and the grid dependence falls below the minimum threshold, the system performs Reactivation to restore the previously controlled equipment. This includes:

- stopping battery discharge
- removing the restriction set on WALM-based loads
- reopening binary controlled consumer

This control sequence helps reduce energy cost, avoid demand penalties, and restore normal operating conditions once the grid situation has returned to an acceptable level.

## 4. Surplus Management and Renewable Utilization

When generation exceeds local demand, MEMS can take action to use that surplus effectively instead of wasting it or exporting unnecessarily. This is especially relevant for renewable generation, where the available power may vary strongly with weather and usage patterns.

Examples of surplus management include:

- charging batteries when renewable generation is high
- removing the restriction set on WALM-based loads
- opening binary controlled consumer

The result is a more efficient microgrid that makes better use of local generation and reduces dependence on external energy sources.

## 5. Alarm Handling

MEMS monitors operating conditions and raises alarms when the system reaches the configured limits for the supported grid-connected control strategies.

The alarm mechanisms currently described in the product scope are limited to:

- Peak Load alarms generated when the grid import or demand approaches the configured peak limit
- general alarm configuration provided through VC Hub, which allows the operator to view and manage standard device and system alarms in the integrated platform

## 6. Reporting, Traceability, and Operational Insight

For an energy management system, visibility is as important as control. MEMS records operating data and sensitive events so that operators can review what happened and why.

This traceability helps operators improve their operating strategy, diagnose faults, and document the performance of the microgrid over time.

## Summary

The main functions of MEMS are to supervise, coordinate, optimize, and monitor the microgrid as a unified energy system. By combining real-time monitoring, storage control, generation coordination, load demand management, peak management, and operational safety logic, MEMS enables stable and efficient grid-connected microgrid operation in normal and constrained conditions.

In short, MEMS acts as the control and optimization layer between energy sources, storage, loads, and the grid. Its purpose is to ensure that the microgrid can operate safely, reliably, and economically while making the best use of available renewable and stored energy resources under grid-connected operation.
