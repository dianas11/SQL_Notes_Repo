# How to Query data?

The SELECT statement is the first thing we are usually shown when we start using SQL in the workplace.

And to retrieve data from a SQL database, we need to write SELECT statements, which are often colloquially refered to as queries. 
A query in itself is just a statement which declares what data we are looking for, where to find it in the database, and optionally, how to transform it before it is returned. 

```
SELECT *
FROM schema.table_name
```

To be able to select different columns from the table and not the table entirely, we specify the names of the columns as below.

```
SELECT column_name_1, 
       column_name_2
FROM schema.table_name
```

For most SQL SERVER T-SQL statements, it is not mandatory to use a semicolon as the statement terminator. Having said that, according to Microsoft documentation a semicolon will be required in future versions of SQL Server.

The semicolon character is a part of the *ANSI SQL _92* standard but was never used with Transact-SQL.
But PostgreSQL requires you to end every query with a semicolon in order to terminate it.

You'll find more details about the usage of semicolon in the appendix section.


### SELECT- How to do calculations within rows

```
SELECT 
    Product_Name, 
    Unit_Price, 
    Units_In_Stock, 
    Unit_Price*Units_In_Stock
FROM ProductsTable
```
When you run the above code, you'll see in the last column, the total value of the stock which the company holds for each product type. Using '*' character between two fields tells the computer to multiply the values on each row of both the columns and present the result in the last column.

A modification that can be done is use of "AS" keyword, an alias which will provide a heading to the column which shows the multiplication result.

```
SELECT 
    Product_Name, 
    Unit_Price, 
    Units_In_Stock, 
    Unit_Price*Units_In_Stock as Stock_Value
FROM ProductsTable
```

### SELECT Without FROM
Before getting any further, it is important to know that "SELECT" can run without "FROM".
For example, try the below code:
```
SELECT 10/2
```
Output: 5

##### Brackets:
 To do more complex calculations, you can make use of brackets. 

```
SELECT (2+2)*5
```

##### Text Strings

The "+" sign has a different use
```
SELECT Address + City
FROM CustomersTable
```
It will show both values for each row, but in one column. This query will show values without any formatting characters i.e., spaces or commas. Below query can fix the problem.
```
SELECT Address + ',' + City
FROM CustomersTable
```

##### FUNCTIONS
A function is something which returns a value.
```
SELECT GetDate()
```
This will return the current date and time.


## The Concept of NULL

A null value is the computer equivalent of a blank space. There are many cases for which we want to replace null with something more useful and here *IsNull* funtion comes in picture.

```
SELECT E.Name as Employee, ISNULL(M.Name, "No Manager") AS Manager
FROM Employee E
LEFT JOIN Employee M
ON E.ManagerId = M.EmployeeId
```

The ISNULL function takes two parameters i.e., ISNULL(expression, replacement_value).

The expression you pass in, if that expression returns null then the replacement value will be used.
In the above example, ISNULL() returns "No Manager" if M.Name value is empty or null.




