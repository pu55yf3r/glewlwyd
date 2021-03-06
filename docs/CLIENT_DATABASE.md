# Glewlwyd Client Module Database Backend documentation

[![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/80x15.png)](https://creativecommons.org/licenses/by/4.0/)

![mod-client-database](screenshots/mod-user-database.png)

The database backend uses a database to store information and passwords for clients. The database can be the same one as the Glewlwyd database or another database of another supported type.

## Installation

In the administration page, go to `Parameters/Clients data sources` and add a new client module by clicking on the `+` button. In the modal, enter a name and a display name (the name must be unique among all client backend instances).
Select the type `Database backend client module` in the Type drop-down button.

Below is the definition of all parameters.

### Name

Name (identifier) of the module instance, must be unique among all the client backend module instances, even of a different type.

### Display name

Name of the instance displayed to the client.

### Read only

Check this option if you want to use this backend as read-only. All client properties such as e-mail, name, password, scopes can't be modifier with Glewlwyd, even administrators.

### Use the same connection as Glewlwyd server

Uncheck this option if you want to use a different database that will store the clients. The new database must have the structure already present. Use one of the following script to initialize the database:

- MariaDB: [database.mariadb.sql](../src/client/database.mariadb.sql)
- Postgre SQL: [database.postgre.sql](../src/client/database.postgre.sql)
- SQLite 3: [database.sqlite3.sql](../src/client/database.sqlite3.sql)

### Database type

This option is available if the option `Use the same connection as Glewlwyd server` is disabled.
Select the database backend among the ones available.

### Path to the database (SQLite 3)

This option is available if the database type selected is SQLite 3.
Enter the path of the SQLite 3 database on the server.

### Host (MariaDB/MySQL)

This option is available if the database type selected is MariaDB/MySQL.
Hostname of the MariaDB/MySQL server.

### Clientname (MariaDB/MySQL)

This option is available if the database type selected is MariaDB/MySQL.
Clientname to connect to the MariaDB/MySQL server.

### Password (MariaDB/MySQL)

This option is available if the database type selected is MariaDB/MySQL.
Password to connect to the MariaDB/MySQL server.

### Database name (MariaDB/MySQL)

This option is available if the database type selected is MariaDB/MySQL.
Name of the database hosting the Glewlwyd client backend tables.

### TCP Connection port (0: system default) (MariaDB/MySQL)

This option is available if the database type selected is MariaDB/MySQL.
TCP Port used to connect to the MariaDB/MySQL database. Set 0 if you want to use default system port.

### Postgre SQL connection string (PostgreSQL)

This option is available if the database type selected is PostgreSQL.
SQL Connection string used to connect to the PostgreSQL database.

### Specific data format

This section allows to specify new properties for the client. The properties may be available for schemes, plugins, in the admin page or in the profile page. By default, when you add a new client backend, the properties `redirect_uri` and `authorization_type` are added with multiple values and read/write modes.

#### Property

Property name, ex: `phone`, `address`, `human`, etc.

#### Multiple values

If this option is checked, the property values will be available as an array of string values, otherwise a single string value.

#### Read (admin)

If this option is checked, plugins and administrators can have access to this property in read mode.

#### Write (admin)

If this option is checked, plugins and administrators can have access to this property in write mode.
