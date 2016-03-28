# [SQLite3](https://www.sqlite.org) wrapper for AutoHotkey_H

### Create an SQLite3 instance
###### sql := SQLite3(options:="", dll:="")
* **options**  -  [Configuration Options](https://www.sqlite.org/c3ref/c_config_covering_index_scan.html). This can be an object with parameters for option or an object with objects if you have multiple options with parameters
* **dll** - the path and name of sqlite3 dll, default for Win32w is sqlite3_x86.dll and sqlite3_x64.dll for x64w. The dll can be loaded from Resources as well (e.g. when compiled) using for example **FileInstall,sqlite3_x86.dll,?**


### Open Database
###### sql.open16[Database,DatabaseHandle]
* **Database** - A path to a database file on disk or network, use ":memory:" to create a database from memory.
* **DataBaseHandle** - the name of the variable in which to store the database handle

### Create Table from Object, File, String or ADO source
###### sql.TableFromObj(hDB, source, table, head:="", delete:=true, primary:="")
###### sql.TableFromFile(hDB, source, table, head:="", delimiter:="`t", skip:=0, trim:="", delete:=true, primary:="")
###### sql.TableFromString(hDB, ByRef source, table, head:="", delimiter:="`t", skip:=0, trim:="", delete:=true, primary:="")
###### sql.TableFromADO(hDB, Connection, Query, table, head:="", delete:=1, primary:="" )
* **hDB** - database handle
* **source** - object, path to a file or string to create the database items from
* **Connection** - ADO connection string
* **Query** - ADO query
* **table** - name of the table to create, if table exists it will be deleted before
* **head** - column definition, e.g. Col1 text, Col2 int, Col3 blob
* **delimiter** - delimiter used for columns in file or string
* **skip** - how many lines in source to skip (exclude)
* **trim** - character to trim items, e.g. omit " for "item"
* **delete** - true if table should be deleted / recreated
* **primary** - primary column(s).

### Query the database
###### sql.SQLToObj(hDB, SQL, column:=false)
###### sql.SQLToString(hDB, SQL, column:=true, separator:="`t", end:="`r`n")
###### sql.SQLToFile(hDB, SQL, path, column:=true, separator:="`t", end:="`r`n")
###### sql.SQLToADO(hDB, SQL, Connection, Table, delete:=true, head:="")
* **hDB** - database handle
* **SQL** - SQL statement. E.g. "Select * from MyTable"
* **path** - file to save data to (content of file will be deleted before)
* **column** - true to include column in output, false to output without header
* **separator** - column separator
* **end** - new line character(s)
* **Connection** - ADO connection string
* **Table** - table name for ADO
* **delete** - delete table (ADO)
* **head** - column definition for ADO

### Execute SQL statement
###### sql.Execute(hDB, SQL)
* **hDB** - database handle
* **SQL** - SQL statement to execute

### Show SQL Query result in ListView
###### sql.List(hDB, SQL, BlobToHex:=false)
* **hDB** - database handle
* **SQL** - SQL Query
* **BlobToHex** - convert blob entries to hex

### Column Declaration type for Table
###### sql.TableDeclType(hDB, Table)
* **hDB** - database handle
* **table** - Table name

### SQL Query data type
###### sql.SQLType(hDB, SQL)
* **hDB** - database handle
* **SQL** - SQL statement
