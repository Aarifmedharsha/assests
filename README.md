# Employee Performance Tracking System

## Overview
Case Study no : 43 [Click here to view the case study](https://github.com/trinity2040/CSD-Case-Study-Repo/blob/main/Group%205-Python%20cluster/CaseStudy_No%20(43).docx)

This project is a console application for tracking employee performance using Python. It includes functionalities to add, update, and delete employee records, update performance scores, and generate performance reviews. Additionally, it uses MySQL to store and manage employee data.

I have also included a python file which runs standalone without the SQL connectivity.

## Prerequisites

### Python
- Python 3.9 or later
- pip (Python package installer)

### MySQL
- MySQL server , workbench or command line client.

## Setup Instructions

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
    

4. *Insert sample data to test queries:(This can also be done in python)*
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

### Python Setup

1. *Install the required Python packages:*
    ```sh
    pip install mysql-connector-python
    pip install pandas
    ```
    
2. *Change host,database,root,pass*
   - Go to the `configs.py` file and change the value of the `GLOBAL_VARIABLES` present in the file according.
   - Example Usage :
     ```sh
     HOST = "localhost"
     DATABASE = "EmployeePerformanceDB"
     USER = "root"
     PASSWORD = "root"
     ```
     


## Running the Application

To run the console application:

```sh
python Main.py
```

And follow the steps according.
