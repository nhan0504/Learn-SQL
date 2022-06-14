# SQL
## **Overview**
### **What is SQL**
- SQL (Structured Query Language): A standard language for relational database
- A non-procedural language -> Won't be able to write application with it
- Usage:
  - Read/retrieve data
  - Write data: Add data to a table
  - Update data: Insert new data
### **Relational database vs Transactional database**

| <center> Relational             | <center> Transaction |
--------------------------------|---------------------
| Show relatinship between tables | More like operational database |
| Optimize for query -> Easier to access data | Good for reading and writting rows quickly |

## **Data model building blocks**

| <center> Entity | <center> Attribute | <center> Relationship |
-------|-----------|-------------
|Person, place, event, ... that are unique and distinguishable | Characteristic of an entity | Relation between entities |
|||One-to-many (Eg: 1 costumers have many invoices) |
|||Many-to-many (Eg: Many students to many classes: 1 student can belong to many classes, and 1 class can have many students) |
|||One-to-one (Eg: Each store has 1 manager) |

### **Primary key and Foreign key**
- Primary key: A column (set of columns) whose values uniquely identify every row in the tables
- Foreign key: One or more columns to identify a row in another table    
## **ER Diagram**
![ER Diagram](Diagram.JPG "Example diagram")

![ER Diagram Notation](Notation.JPG "Relationship notations")

## Retrieve data
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