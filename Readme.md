# CSE3122: Database Management Lab

## Database Manipulation

### Create Database
``` sql
CREATE DATABASE [IF NOT EXISTS] database_name;
```

### Delete Database
``` sql
DROP DATABASE [IF EXISTS] database_name;
```
### Use Database
``` sql
USE database_name;
```
## Table Manipulation

### Create Table
``` sql
CREATE TABLE [IF NOT EXISTS] table_name(
    field_name ATTRIBUTES,
    field_name ATTRIBUTES,
    field_name ATTRIBUTES,
    .....................,
    .....................,
    field_name ATTRIBUTES
); 
```

### Delete Table
``` sql
DROP TABLE [IF NOT EXISTS] table_name;
```
### Insert Row(s) into Table
``` sql
INSERT INTO table_name (field1, field2,...fieldN)
    VALUES
        (value11, value12,..,value1N),
        (value21, value22,..,value2N),
        ............................,
        (valueM1, valueM2,..,valueMN);
```

### Rename Table
``` sql
ALTER TABLE table_name
    RENAME TO new_table_name;
```

### Rename Column
``` sql
ALTER TABLE table_name 
    CHANGE COLUMN old_column_name new_column_name DATATYPE(LENGTH);
```

### Select Query
``` sql
SELECT field1, field2,...fieldN 
    FROM table_name1, table_name2...
```
### Where Clause
``` sql
SELECT field1, field2,...fieldN table_name1, table_name2...
    [WHERE condition1 [AND [OR]] condition2.....
```

### Update Query
``` sql
UPDATE table_name SET 
    field1 = new-value1, 
    field2 = new-value2
        [WHERE Clause]
```

### Delete Row(s)
``` sql
DELETE FROM table_name 
    [WHERE Clause]
```

