# Least-Privilege Database Accounts

VC Hub connects to external databases with credentials supplied by the user. The database server controls the permissions associated with those credentials.

Use a dedicated database account for each VC Hub connection and grant only the permissions required for that connection's purpose. Do not use a database administrator or server administrator account for routine VC Hub operation.

## General Recommendations

- Create a dedicated account for VC Hub instead of sharing an account with another application or person.
- Restrict the account to the required database, schema, bucket, or organization.
- Do not use built-in administrator accounts such as MySQL `root`, SQL Server `sa`, PostgreSQL `postgres`, or an InfluxDB owner/operator token.
- Do not grant user-management, server-configuration, backup, restore, replication-management, or operating-system privileges.
- Use a strong, unique password or token and rotate it according to your organization's security policy.
- Require an encrypted database connection when the database supports TLS.
- Restrict network access so that the database accepts connections only from the required VC Hub hosts.
- Store credentials only in the VC Hub database connection configuration. Do not place credentials in scripts, screenshots, or documentation.
- Periodically review the account and remove permissions that are no longer required.

## Select Permissions by Connection Purpose

The required permissions depend on how the connection is used.

| Connection purpose | Typical permissions |
|---|---|
| Query existing data | Connect and read the required tables, views, schemas, buckets, or measurements |
| Store and query history data | Connect, read, insert, update, and delete data in the dedicated history-data scope |
| Let VC Hub create or maintain its history schema | The preceding data permissions plus only the schema or object-creation permissions required in the dedicated VC Hub scope |
| Execute user-configured SQL that changes data | Only the specific data-modification permissions required by those queries |

Start with read-only access when the connection is used only to query existing data. Do not grant write or schema-management permission unless a configured VC Hub function requires it.

Some history database functions may create tables, indexes, partitions, retention objects, or other database-specific objects. If VC Hub manages these objects, grant the necessary object-management permissions only within a database or schema dedicated to VC Hub. Do not grant equivalent permissions at the database-server or cluster level.

## Provisioning and Runtime Accounts

Where supported by the database and your operational process, use separate accounts:

1. A temporary provisioning account that creates the database objects required by VC Hub.
2. A runtime account with only the read and write permissions required after provisioning.

Remove or disable the provisioning account after setup if it is no longer needed. If upgrades require schema changes, enable the provisioning permissions only for the maintenance window and remove them afterward.

## Verify the Account

Before production use:

1. Confirm that VC Hub can connect with the dedicated account.
2. Test each configured operation, such as querying data or writing history data.
3. Confirm that operations outside the intended database or schema are denied.
4. Confirm that the account cannot create users, grant roles, modify server settings, or access unrelated databases.
5. Review database audit logs for unexpected permission failures or privileged operations.

If a VC Hub operation fails because of insufficient permission, identify the exact denied database operation and grant only that permission in the required scope. Do not resolve the error by assigning a database administrator role.

Refer to the security and authorization documentation supplied by the database vendor for the exact role, grant, and token syntax supported by your database version.
