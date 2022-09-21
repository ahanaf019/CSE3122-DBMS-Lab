# CSE3122: Database Management Lab

## Contents

1. [Database Manipulation](#database-manipulation)
1. [Table Manipulation](#table-manipulation)
1. [Queries](#queries)
1. [Triggers](#triggers)
1. [Show Command](#show-command)
1. [Locking](#locking)
1. [Join Operations](#join-operations)
1. [Aggrigate Functions](#aggrigate-functions)
1. [Regular Expressions](#regular-expressions)
1. [MySQL Constraints](#mysql-constraints)
1. [User Manipulation](#user-manipulation)
1. [Others](#others)

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

## Locking
For InnoDB Engine
### Table Locking
``` sql
LOCK TABLES tab_name1 [READ | WRITE],   
            tab_name2 [READ | WRITE],
            ...... ;  
```
### Unlock Tables
``` sql
UNLOCK TABLES;  
```

## Join Operations
```sql
SELECT table1.field1, table2.field1, table1.field2
    FROM table1
    [INNER JOIN / LEFT JOIN / RIGHT JOIN / CROSS JOIN] table2 
        ON table1.fieldM=table2.fieldN;
```
| Type | Description |
| --- | --- |
| `INNER JOIN` | Returns records that have matching values in both tables |
| `LEFT JOIN` | Returns all records from the left table, and the matched records from the right table |
| `RIGHT JOIN` | Returns all records from the right table, and the matched records from the left table |
| `CROSS JOIN` | Returns all records from both tables |

## Aggrigate Functions

| Aggregate Function |	Descriptions |
| ------------------ | ------------- |
| `count()` |	Returns the number of rows, including rows with NULL values in a group. |
| `sum()` |	Returns the total summed values (Non-NULL) in a set. |
| `average()` |	Returns the average value of an expression. |
| `min()` |	Returns the minimum value in a set. |
| `max()` |	Returns the maximum value in a set. |
| `groutp_concat()` |	Returns a concatenated string. |
| `first()` |	Returns the first value of an expression. |
| `last()` |	Returns the last value of an expression. |


## Regular Expressions

| Pattern |	Match |
| ------- | ----- |
| `^` |	Beginning of string |
| `$` |	End of string |
| `.` |	Any single character |
| `[...]` |	Any character listed between the square brackets |
| `[^...]` |	Any character not listed between the square brackets |
| `p1\|p2\|p3` |	Alternation; matches any of the patterns p1, p2, or p3 |
| `*` |	Zero or more instances of preceding element |
| `+` |	One or more instances of preceding element |
| `{n}` |	n instances of preceding element |
| `{m,n}` |	m through n instances of preceding element |
| `[abc]` |	Any character listed between the square brackets |
| `[^abc]` |	Any character not listed between the square brackets |
| `[A-Z]` |	match any upper case letter. |
| `[a-z]` |	match any lower case letter |
| `[0-9]` |	match any digit from 0 through to 9. |
| `?` |	Match zero or one instances of the strings preceding it. |

## MySQL Constraints
| Constraint | Description |
| ---------- | ----------- |
| `NOT NULL` | Ensures that a column cannot have a NULL value |
| `UNIQUE` | Ensures that all values in a column are different |
| `PRIMARY KEY` | A combination of a NOT NULL and UNIQUE. Uniquely identifies | each row in a table |
| `FOREIGN KEY` | Prevents actions that would destroy links between tables |
| `CHECK` | Ensures that the values in a column satisfies a specific condition |
| `DEFAULT` | Sets a default value for a column if no value is specified |
| `CREATE INDEX` | Used to create and retrieve data from the database very quickly |
| `AUTO_INCREMENT` | Automatically generates a unique number when inserting a new record. |

## User Manipulation
### Create User
```sql
CREATE USER 'uname'@'hostname' IDENTIFIED BY 'password';
```
### Grant Permission to User
```sql
GRANT [ALL / privilage_list] on database_name.table_name TO 'uname'@'hostname' [WITH GRANT OPTION];
```

### Flush
```sql
FLUSH PRIVILEGES;
```

### Revoke Permission from User
```sql
REVOKE type_of_permission ON database_name.table_name FROM 'uname'@'hostname';
```

### Show Granted Permission to User
```sql
SHOW GRANTS FOR 'uname'@'hostname';
```

### Delete User
```sql
DROP USER 'uname'@'hostname';
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