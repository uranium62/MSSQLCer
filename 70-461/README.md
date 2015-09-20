# MS SQL 70-461

### Change scope db

```sql
USE NuggerDemoDB
GO
```

### Add new columns

```sql
ALTER TABLE Employees
	ADD
		ActiveFlag bit NOT NULL,
		ModifiedDate datetime NOT NULL
```

### Change the type of column

```sql
ALTER TABLE Products
	ALTER COLUMN Price money
```

### Change name

```sql
EXEC sp_rename 'Sales', 'SaleOrder'

EXEC sp_rename 
	@objectname = 'TableName.OldColumnName',
	@newname = 'NewColumnName',
	@objtype = 'COLUMN'
```


### Create a table

```sql
CREATE TABLE Employees
(
	EmployeeID int NOT NULL,
	FirstName nvarchar(50) NOT NULL,
	MiddleName nvarchar(50) NULL,
	LastName nvarchar (75) NOT NULL,
	Title nvarchar(100) NULL,
	HireDate datetime NOT NULL,
	VacationHours smallint NOT NULL,
	Salary decimal (19,4) NOT NULL,

)
```

### Delete column

```sql
ALTER TABLE Products
	DROP COLUMN Price	
```

### Drop a table

```sql
DROP TABLE Employees
```

### Create a view

```sql
CREATE VIEW vEmployeesWithSales
AS 

	SELECT DISTINCT
		Employees.*
	FROM 
		Employees
			JOIN 
			Sales ON Employees.EmployeeID=Sales.EmployeeID

GO
	
```