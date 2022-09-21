# CSE3122: Database Management Lab

## Contents

1. [Database Manipulation](#database-manipulation)
1. [Table Manipulation](#table-manipulation)
1. [Queries](#queries)
1. [Triggers](#triggers)
1. [Show Command](#show-command)
1. [Others](#others)
1. [Link to Header](#queries)

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
    column1 DATATYPE CONSTRAINT,
    column2 DATATYPE CONSTRAINT,
    column3 DATATYPE CONSTRAINT,
    ....
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

### Add Column
``` sql
ALTER TABLE table_name
    ADD column_name_1 datatype,
    ADD column_name_2 datatype,
    ...;
```

### Delete Column
``` sql
ALTER TABLE table_name
    DROP COLUMN column_name_1,
    DROP COLUMN column_name_2,
    ...;
```


## Queries

### Select Query
``` sql
SELECT field1, field2,...fieldN 
    FROM table_name1, table_name2...
```
### Where Clause
``` sql
SELECT field1, field2,...fieldN 
    FROM table_name1, table_name2...
        [WHERE condition1 [AND [OR]] condition2.....
```

### Like Clause
``` sql
SELECT field1, field2,...fieldN 
    FROM table_name1, table_name2...
        WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

### Group By Clause
``` sql
SELECT field1, field2,...fieldN
    FROM table_name1, table_name2...
        WHERE condition
            GROUP BY column_name(s)
```

### Having Clause (Used with aggrigate functions)
``` sql
SELECT field1, field2,...fieldN
    FROM table_name1, table_name2...
        WHERE condition
            GROUP BY column_name(s)
                HAVING condition;
```


### Order Query Results
``` sql
SELECT field1, field2,...fieldN 
    FROM table_name1, table_name2...
        ORDER BY field1, [field2...] [ASC [DESC]]
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

## Triggers

### Creating a Trigger
``` sql
DELIMITER $$
CREATE TRIGGER trigger_name    
    (AFTER | BEFORE) (INSERT | UPDATE | DELETE)  
         ON table_name FOR EACH ROW    
         BEGIN    
        --variable declarations    
        --trigger code    
        END$$     
```

## SHOW Command

### List Triggers
```sql
SHOW TRIGGERS;
```

### Show Trigger Definition
```sql
SHOW CREATE TRIGGER trigger_name;
```

### List Columns of a Table
```sql
SHOW COLUMNS FROM table_name;
```

### Show Table Definition
```sql
SHOW CREATE TABLE table_name;
```

### List Databases/Schemas
```sql
SHOW DATABASES/SCHEMAS;
```

### Show Server's Storage Engines
```sql
SHOW ENGINES;
```

### Show Server Status
```sql
SHOW STATUS;
```

### List Supported Privilages 
``` sql
SHOW PRIVILEGES;
```

## Others

### Connection ID
```sql
SELECT CONNECTION_ID();
```

### MySQL Version Check
`mysql -v`

### MySQL Command Line Login
`mysql -u [username] -p`