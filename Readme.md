# SQL

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

## CURD Operations

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

# DATABASE

## WHAT IS DATA?

Any sort of information that is stored is called data.
There are many types of data like contact details, credentials, messages, emails, etc.
Not only the conventional type but also users activity on a web application can be called as data.  
Companies mine this data i.e they get useful inforamtion like product reviews, popularity of a product etc.
