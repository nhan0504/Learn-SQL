- [Overview](#overview)
  - [What is SQL](#what-is-sql)
  - [Relational database vs Transactional database](#relational-database-vs-transactional-database)
- [Data model building blocks](#data-model-building-blocks)
  - [Primary key and Foreign key](#primary-key-and-foreign-key)
- [ER Diagram](#er-diagram)
- [Retrieve data](#retrieve-data)
- [Tables](#tables)
  - [Create new table](#create-new-table)
  - [Add data into the table](#add-data-into-the-table)
  - [Delete table](#delete-table)
  - [Truncate table](#truncate-table)
  - [Alter table](#alter-table)
  - [Permission](#permission)
  - [Temporary table](#temporary-table)
- [Comment](#comment)
# Overview
## What is SQL
- SQL (Structured Query Language): A standard language for relational database
- A non-procedural language -> Won't be able to write application with it
- Usage:
  - Read/retrieve data
  - Write data: Add data to a table
  - Update data: Insert new data
## Relational database vs Transactional database

| <center> Relational             | <center> Transaction |
--------------------------------|---------------------
| Show relatinship between tables | More like operational database |
| Optimize for query -> Easier to access data | Good for reading and writting rows quickly |

# Data model building blocks

| <center> Entity | <center> Attribute | <center> Relationship |
-------|-----------|-------------
|Person, place, event, ... that are unique and distinguishable | Characteristic of an entity | Relation between entities |
|||One-to-many (Eg: 1 costumers have many invoices) |
|||Many-to-many (Eg: Many students to many classes: 1 student can belong to many classes, and 1 class can have many students) |
|||One-to-one (Eg: Each store has 1 manager) |

## Primary key and Foreign key
- Primary key: A column (set of columns) whose values uniquely identify every row in the tables
- Foreign key: One or more columns to identify a row in another table    
# ER Diagram
![ER Diagram](Diagram.JPG "Example diagram")

![ER Diagram Notation](Notation.JPG "Relationship notations")

# Retrieve data
- SELECT statement has 2 components: What you want and where you want to select it from
- Retrieve data about product from a table named Products
``` SQL
SELECT prod_name,
       prod_id,
       prod_price
FROM Products;
```
- Get all the columns in table Products
``` SQL
SELECT *
FROM Products;
```
- Get first 5 rows from table Products
``` SQL
SELECT prod_name
FROM Products
LIMIT 5;
```

# Tables
## Create new table
- Specify what data type can be accepted (Eg: NULL -> Accept NULL value)
``` SQL
CREATE TABLE Shoes
    (
    Id          char(10)        PRIMARY KEY,
    Brand       char(10)        NOT NULL,
    Color       char(250)       NOT NULL,
    Price       decimal(8,2)    NOT NULL,
    Descript    Varchar(750)    NULL
    );
```
## Add data into the table
``` SQL
INSERT INTO Shoes
       (
        Id,
        Brand,
        Color,
        Price,
        Descript
       )
VALUES ('892071',
        'Gucci',
        'Pink',
        '695.00',
        NULL
       );
```

## Delete table
``` SQL
DROP TABLE Shoes;
```

## Truncate table
Clear all the data in the table
``` SQL
TRUNCATE TABLE Shoes;
```

## Alter table
Edit an existing table like adding columns, rename, ...
``` SQL
ALTER TABLE Shoes RENAME TO products;
```

## Permission
``` SQL
-- Grant permission
GRANT ALL PRIVILEGES ON Shoes TO authorized_users;
-- Remove access
REVOKE ALL PRIVILEGES ON Shoes TO authorized_users;
```

## Temporary table
- Temporary table will be deleted when current session terminate
- Benefit of temporary table
  - Faster than creating a real table
  - Useful for complex queries using subset of tables and joins   

Create a temporary table from a subset of another table
``` SQL
CREATE TEMPORARY TABLE Sandals AS
    (
        SELECT *
        FROM shoes
        WHERE shoe_type = 'sandals'
    )
```

# Comment
<big> Single line comment: 2 dashes
<small>
``` SQL
SELECT prod_name,
     --prod_id,
       prod_price
FROM Products;
```
<big> Multi-line commnent
<small>
``` SQL
SELECT prod_name,
    /* prod_id,
       prod_price
    */
FROM Products;
```