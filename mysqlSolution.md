### MySQL Setup
1. *Start MySQL server* and log in as root(User defined):
    ```sh
    mysql -u root -p
    

2. *Create the database and tables:*
    ```sql
    CREATE DATABASE EmployeePerformanceDB;
    ```
    ```sql
    USE EmployeePerformanceDB;
    ```
    ```sql
    CREATE TABLE Employees (
        employee_id INT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        department VARCHAR(50) NOT NULL,
        designation VARCHAR(50) NOT NULL,
        performance_score INT NOT NULL
    );
    ```
    ```sql
    CREATE TABLE PerformanceReviews (
        review_id INT PRIMARY KEY AUTO_INCREMENT,
        employee_id INT,
        review_date DATE,
        review_comments TEXT,
        FOREIGN KEY (employee_id) REFERENCES Employees(employee_id)
    );
    ```
    

3. *Insert sample data to test queries:(This can also be done in python)*
    ```sql
    INSERT INTO Employees (employee_id, name, department, designation, performance_score)
    VALUES 
    (1, 'Aarif M', 'Sales', 'Manager', 90),
    (2, 'Varshaa N', 'IT', 'Developer', 88),
    (3, 'Yeshwant M', 'HR', 'Executive', 82),
    (4, 'Robin Saji', 'Sales', 'Representative', 95),
    (5, 'Sidharth T', 'Sales', 'Manager', 87),
    (6, 'Asswin C', 'Sales', 'Representative', 92),
    (7, 'Saran K', 'Sales', 'Executive', 88),
    (8, 'Jeevan R', 'Sales', 'Representative', 91),
    (9, 'Ashraf M', 'IT', 'Manager', 84),
    (10, 'Sathya P', 'HR', 'Executive', 75);
    ```
    ```sql
    INSERT INTO PerformanceReviews (review_id, employee_id, review_date, review_comments)
    VALUES 
    (1, 1, '2024-01-01', 'Excellent performance'),
    (2, 2, '2024-01-05', 'Good performance'),
    (3, 2, '2024-03-10', 'Consistent performance'),
    (4, 2, '2024-06-15', 'Improved performance'),
    (5, 3, '2024-02-20', 'Needs improvement'),
    (6, 4, '2024-01-25', 'Outstanding performance'),
    (7, 5, '2024-03-30', 'Average performance'),
    (8, 6, '2024-04-10', 'Excellent performance'),
    (9, 7, '2024-05-05', 'Good performance'),
    (10, 7, '2024-06-01', 'Consistent performance'),
    (11, 7, '2024-07-10', 'Improved performance'),
    (12, 7, '2024-08-15', 'Outstanding performance'),
    (13, 1, '2024-09-10', 'Satisfactory performance'),
    (14, 4, '2024-09-20', 'Exemplary performance'),
    (15, 5, '2024-09-25', 'Consistent performance'),
    (16, 6, '2024-09-30', 'Excellent performance'),
    (17, 8, '2024-10-05', 'Outstanding performance'),
    (18, 8, '2024-10-10', 'Consistent performance'),
    (19, 8, '2024-10-15', 'Good performance'),
    (20, 8, '2024-10-20', 'Satisfactory performance');
    ```
### MySQL Queries

1. *Write a query to find the average performance score of employees in each department.*
    ```sql
    SELECT department, AVG(performance_score) AS average_performance_score
    FROM Employees
    GROUP BY department;
    ```
    *Output:*
   
    ![image](https://github.com/Aarifmedharsha/assests/blob/main/Query1.png)

3. *Write a query to find the names and performance scores of employees along with their departments.*
    ```sql
    SELECT e.name, e.performance_score, e.department
    FROM Employees e;
    ```
    *Output:*
   
    ![image](https://github.com/Aarifmedharsha/assests/blob/main/Query2.png)

4. *Write a query to find the names of employees who have never had a performance review.*
    ```sql
    SELECT e.name
    FROM Employees e
    LEFT JOIN PerformanceReviews pr
    ON e.employee_id = pr.employee_id
    WHERE pr.employee_id IS NULL;
    ```
    *Output:*
   
    ![image](https://github.com/Aarifmedharsha/assests/blob/main/Query3.png)

5. *Write a query to find the departments that have more than 5 employees with performance scores greater than 85.*
    ```sql
    SELECT department
    FROM Employees
    WHERE performance_score > 85
    GROUP BY department
    HAVING COUNT(employee_id) > 5;
    ```
    *Output:*
   
    ![image](https://github.com/Aarifmedharsha/assests/blob/main/Query4.png)

6. *Write a query to find the names and designations of employees who have had more than 3 performance reviews.*
    ```sql
    SELECT e.name, e.designation
    FROM Employees e
    JOIN PerformanceReviews pr ON e.employee_id = pr.employee_id
    GROUP BY e.employee_id
    HAVING COUNT(pr.review_id) > 3;
    ```
    *Output:*
   
    ![image](https://github.com/Aarifmedharsha/assests/blob/main/Query5.png)
