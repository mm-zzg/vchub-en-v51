# Supported Data Types

SQL Query in each database only support the following data types.

## **SQLite**

| **Data Type** | **Description**                                                       |
|---------------|-----------------------------------------------------------------------|
| INTEGER       | Integer type                                                          |
| NUMERIC       | A general type that can be an integer, floating-point number, or date |
| REAL          | Floating-point number type                                            |
| TEXT          | Text data type                                                        |

## **MySQL**

| **Data Type**      | **Description**                      |
|--------------------|--------------------------------------|
| BIGINT             | Large integer type                   |
| BIGINT UNSIGNED    | Unsigned large integer type          |
| BIT                | Bit type                             |
| BOOL               | Boolean type                         |
| CHAR               | Fixed-length character type          |
| DATE               | Date type                            |
| DATETIME           | Date time type                       |
| DECIMAL            | Exact decimal type                   |
| DOUBLE             | Double precision floating-point type |
| DOUBLE PRECISION   | Double precision floating-point type |
| ENUM               | Enumeration type                     |
| FLOAT              | Single precision floating-point type |
| INT                | Integer type                         |
| INT UNSIGNED       | Unsigned integer type                |
| INTEGER            | Integer type                         |
| INTEGER UNSIGNED   | Unsigned integer type                |
| LONG VARCHAR       | Long text type                       |
| LONGTEXT           | Long text type                       |
| MEDIUMINT          | Medium range integer type            |
| MEDIUMINT UNSIGNED | Unsigned medium range integer type   |
| MEDIUMTEXT         | Medium-length text type              |
| NUMERIC            | Exact decimal type                   |
| REAL               | Single precision floating-point type |
| SET                | Set type                             |
| SMALLINT           | Small integer type                   |
| SMALLINT UNSIGNED  | Unsigned small integer type          |
| TEXT               | Variable-length text type            |
| TIME               | Time type                            |
| TIMESTAMP          | Timestamp type                       |
| TINYINT            | Tiny integer type                    |
| TINYINT UNSIGNED   | Unsigned tiny integer type           |
| TINYTEXT           | Short text type                      |
| VARCHAR            | Variable-length string type          |
| YEAR               | Year type                            |
| JSON               | JSON data type                       |

## **SQL Server**

| **Data Type**    | **Description**                         |
|------------------|-----------------------------------------|
| bigint           | Large integer type                      |
| bit              | Bit type                                |
| char             | Fixed-length character type             |
| date             | Date type                               |
| datetime         | Date time type                          |
| datetime2        | Precise date time type                  |
| datetimeoffset   | Date time type with time zone awareness |
| decimal          | Exact decimal type                      |
| float            | Double precision floating-point type    |
| int              | Integer type                            |
| money            | Currency type                           |
| nchar            | Fixed-length Unicode character type     |
| ntext            | Large Unicode text type                 |
| numeric          | Exact decimal type                      |
| nvarchar         | Variable-length Unicode character type  |
| real             | Single precision floating-point type    |
| smalldatetime    | Date time type (with smaller range)     |
| smallint         | Small integer type                      |
| smallmoney       | Small range currency type               |
| sql_variant      | Generic data type                       |
| sysname          | System object name type                 |
| text             | Large ASCII text type                   |
| time             | Time type                               |
| tinyint          | Tiny integer type                       |
| uniqueidentifier | Globally unique identifier (GUID)       |
| varchar          | Variable-length ASCII character type    |
| xml              | XML type                                |

## **PostgreSQL**

| **Data Type**                                 | **Description**                                   |
|-----------------------------------------------|---------------------------------------------------|
| bigint                                        | Large integer type                                |
| bigserial                                     | Auto-incrementing large integer type              |
| boolean                                       | Boolean type                                      |
| character [ (***n*** ) ]                      | Fixed-length character type                       |
| character varying [ (***n*** ) ]              | Variable-length character type                    |
| date                                          | Date type                                         |
| double precision                              | Double precision floating-point type              |
| integer                                       | Integer type                                      |
| json                                          | JSON type                                         |
| jsonb                                         | Binary JSON type                                  |
| numeric [ (p, s) ]                            | Exact decimal type                                |
| real                                          | Single precision floating-point type              |
| smallint                                      | Small integer type                                |
| smallserial                                   | Auto-incrementing small integer type              |
| serial                                        | Auto-incrementing integer type                    |
| text                                          | Text type                                         |
| time [ (***p*** ) ] [ without time zone ]     | Time type, without time zone information          |
| timestamp [ (***p*** ) ] [ without time zone] | Date and time type, without time zone information |
| timestamp [ (***p*** ) ] with time zone       | Date and time type, with time zone information    |
| uuid                                          | Universally Unique Identifier (UUID) type         |
| xml                                           | XML type                                          |

## **InfluxDB**

supports all data types.