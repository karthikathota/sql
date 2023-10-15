# SQL

- SQL is used to work on RDBMS.
- SQL is a declarative( User specifies what should be done rather than how it should be done).
- SQL stands for Structured Query Language
- It is the Language that is used to access database and manage it.
- It is maily of rows and columns scheme
- columns are also called as keys, attributes feilds.
- Rows are also called as records
- The most important part of sql cloumn is the PRIMARY KEY. An SQL column always starts with the primary key and followed by values
- The primary key is important because its can be used for data saving which means when combining two tables we can combine them by the id of the user rather than teh whole data of the user.

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Department VARCHAR(50),
    Salary DECIMAL(10, 2) NOT NULL
);
```

- Here in table there are 2 words NULL and NOT NULL.
  NULL- It states that the value can be empty.
  NOT NULL- It states that we have to always provide the value.

## CRUD Operations

    ABBREVATION  |   SQL
       Create    |   Insert
       Update    |   Update
       Read      |   Select
       Delete    |   Delete

1. CREATE(Inset):-

```sql
INSERT INTO Employees (EmployeeID, FirstName, LastName, Department, Salary)
VALUES (6, 'Sarah', 'Johnson', 'Finance', 5500.00);
```

- This Query creates a new record for the employee table.

2. Read (SELECT):

```sql
SELECT * FROM Employees;
```

- Here star selects all the attributes from the employee table.

```sql
SELECT * FROM Employees WHERE Department = 'IT';
```

- Here we are specifing what attributes to be selected.

3. Update (UPDATE):

```sql
UPDATE Employees
SET Department = 'Marketing', Salary = 6000.00
WHERE EmployeeID = 2;
```

4. Delete (DELETE):

```sql
DELETE FROM Employees
WHERE EmployeeID = 5;
```

## Other Operations

1. Update a value that is already given.

```sql
Update
  Employees
set
  LastName="Athota"
WHERE
  FirstName="Sai";
```

2. Delte a table from database.

```sql
DROP TABLE Employees
```

3. Rename a column.

```sql
ALTER TABLE
  Employees RENAME COLUMN LastName to Fullname;
```

4. Add a new column

```sql
ALTER TABLE
  Employees
ADD
  COLUMN age int;
```

## JOINING TWO TABLES.

- Joining of two tables is a vey important concpet in SQL. It is mainly done by taking the priamry id from the two tables.

TABLE ONE:
EmployeeID | FirstName | LastName | Department | Salary

---

1 | John | Doe | 1 | 5000.00  
2 | Jane | Smith | 2 | 4500.00  
3 | David | Johnson | 3 | 6000.00  
4 | Emily | Williams | 1 | 5500.00  
5 | Michael | Brown | 4 | 4000.00

TABLE TWO:
DepartmentID | DepartmentName

---

1 | IT  
2 | HR  
3 | Sales  
4 | Marketing

```sql
SELECT Employees.EmployeeID, Employees.FirstName, Employees.LastName, Departments.DepartmentName
FROM Employees
JOIN Departments ON Employees.Department = Departments.DepartmentID;
```

- In this example we are joining the two tables with respect to the primary id's.

### Comparison Operators

Equals to => "="  
Not equal to => "<>"  
Greater than => ">"  
Greater than or equals to => ">="  
Less than => "<"  
Less than or equals to => "<="

### String operators

To get all the rows that have matching patters we sue "LIKE".

"%" => If it is in the **end** it matches all the words that start with given word. If it is in the **begning** it matches all the words that end with give word. If the word is **encapsulated** in "%" then matches all the word that contain given word.  
FOR EXAMPLE:-  
"pant%" this matches all the words starting with pants  
"%pant" this matches all the words that end with pants

"_" => This matches all the words that are same with a only charachter mroe than the given word.
FOR EXAMPLE:-  
"pant_" matches word like pants etc, where s is is onlt charachter.

### Logical Operators

1. AND:- Retrives all the rows that statisfy the both given conditions.
2. OR:- Retrives all the rows which statisfy atleast one of the given conditions.
3. NOT:- Retrives all the rows which donot statisfy the given conditions

PRECEDENCE :- NOT > AND > OR

### ORDER BY

Ascending => ASC  
Descending => DESC

## Pagination

These are two clauses in Pagination which are used to limit the data retrieved they are LIMIT AND OFFSET

### LIMIT

LIMIT clause is used to specify the number of rows.

### OFFSET

OFFSET clause is used to specify the position from where to rows are to be selected.

Rows are selected from OFFSET+1 to LIMIT+OFFSET.

## AGREGATIONS

Combining multiple values into a singel value.

sum(c1) => Returns sum of all the values in c1.  
Avg(c1) => Returns avg value of column c1.  
similarly we have MAX,MIN,COUNT etc.

AS => It can be used to provide temporary names for column

```sql
SELECT c1 AS a1,c2 AS a2....
```

### GROUP BY

```sql
SELECT
  name,
  sum(score)
FROM
  PLAYER_MATCH_DETAILS
GROUP BY
  name;

```

## FUNCTIONS

### strftime()

It is a data function which can be used in various clauses to extract month and year from date field.

```sql
strftime(format, field_name);
```

%Y => Extracts the year.  
%m => extracts the month.

Eg :-
Find out the no of cars sold per month in 2020

```sql
select strftime("%m",dates) as month
count(*) as total_cars
where strftime("%Y",dates) == '2020'
group by month
```

# ER MODEL

There 3 main core parts to an ER model they are

1. Entity
2. Entity Type
3. Relationships

### Entity

Real worls objects/models are called as Entities in ER model. Properties of these objects are called as attributes of the entities. Like name and age of a person etc. The uniquely identifiable entities are called as key attributes.

### Entity Type

Collection of entities with same attributes are called as Entity Type.

### Relationships

Association between the entities is called as Relationships. There are 3 types of Relationships in ER MODEL they are **_One-to-One Relationships_**, **_One-to-Many Relationships_**, **_Many-to-one Relationships_**.

### One-to-ONE Relationships

An entity is realated to only one entity.

### One-to-Many Relationships

An entity is realted to many other entities and vice versa.

### Many-to-Many Relationships

Many entities are related to many entities.

### CREATING PRIAMRY KEY

```sql
CREATE TABLE table_name{
  INTEGER NOT NULL PRIMARY KEY,
}
```

### ENABLING FOREIGN KEY

```sql
CREATE TABLE table_name{
  INTEGER NOT NULL PRIMARY KEY,

FOREIGN KEY (column_name) REFERENCES table1(id) ON DELETE CASCADE
}
```

ON DELETE CASCADE specifies that when a row in the referenced table (table1) is deleted, the corresponding rows in the current table will be deleted as well.
