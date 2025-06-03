# AWS-RDS-MySQL-Lab
Full Report

Lab Overview

This project demonstrates how to launch, configure, and interact with an AWS RDS MySQL database instance from an EC2 Linux server.
Key tasks include database creation, table management, data manipulation, and basic SQL queries using best practices in AWS.

Step-by-Step Commands & Outputs

1. Database & Connectivity Setup
Launched RDS MySQL DB (restart-db) with:
Engine: MySQL 8.x (db.t3.micro)
Storage: 20GB General Purpose SSD (gp3)
Lab VPC, proper subnet/security group settings
Created default DB: restartdb
Master user: main
Password: (lab-password123 or your value)
Connected via EC2 (LinuxServer):
ssh -i labsuser-3.pem ec2-user@<EC2-PUBLIC-IP>
2. Connect to RDS MySQL from EC2
mysql -h restart-db.cdnerqw78dn1.us-west-2.rds.amazonaws.com -u main -p
(Enter your password when prompted)

3. Create & Populate Tables
A. Use the Correct Database

USE restartdb;
B. Create Table: RESTART

CREATE TABLE RESTART (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(100),
    RestartCity VARCHAR(100),
    GraduationDate DATETIME
);
C. Insert 10 Sample Rows

INSERT INTO RESTART VALUES
(1, 'Alice Smith', 'Tel Aviv', '2023-06-15 09:00:00'),
(2, 'Bob Cohen', 'Jerusalem', '2023-07-20 10:30:00'),
(3, 'Chen Li', 'Haifa', '2023-08-10 12:00:00'),
(4, 'Dina Katz', 'Eilat', '2023-09-01 11:00:00'),
(5, 'Eli Bar', 'Beer Sheva', '2023-06-25 09:45:00'),
(6, 'Fay Golan', 'Ashdod', '2023-10-05 13:30:00'),
(7, 'Gil Hadad', 'Holon', '2023-11-15 14:00:00'),
(8, 'Hana Levi', 'Nazareth', '2023-12-05 15:30:00'),
(9, 'Idan Mor', 'Petah Tikva', '2023-07-30 09:15:00'),
(10, 'Jacob Klein', 'Netanya', '2023-08-20 10:15:00');
D. View Table Data

SELECT * FROM RESTART;
E. Create Table: CLOUD_PRACTITIONER

CREATE TABLE CLOUD_PRACTITIONER (
    StudentID INT PRIMARY KEY,
    CertificationDate DATETIME
);
F. Insert 5 Sample Rows

INSERT INTO CLOUD_PRACTITIONER VALUES
(1, '2024-03-10 10:00:00'),
(3, '2024-04-12 14:00:00'),
(5, '2024-05-20 13:30:00'),
(7, '2024-06-18 11:00:00'),
(10, '2024-07-25 09:45:00');
G. View Table Data

SELECT * FROM CLOUD_PRACTITIONER;
4. INNER JOIN – Show Students with Certifications
SELECT
  RESTART.StudentID,
  RESTART.StudentName,
  CLOUD_PRACTITIONER.CertificationDate
FROM
  RESTART
INNER JOIN
  CLOUD_PRACTITIONER
ON
  RESTART.StudentID = CLOUD_PRACTITIONER.StudentID;
Screenshots

Attach screenshots of:
Table creation commands
Data insertion
SELECT queries for both tables
INNER JOIN output
Key Takeaways

Hands-on AWS RDS: Deploying and connecting to cloud-managed MySQL.
Linux SSH/CLI: Secure, best-practice cloud access.
SQL Proficiency: Table DDL, data DML, INNER JOINs for relational queries.
Cloud Security: Correct VPC, subnet, security group configuration.
How to Reproduce

Launch RDS MySQL, configure as described.
Launch EC2 Linux in the same VPC.
SSH into EC2; use the provided MySQL connection command.
Run all SQL queries above step-by-step.
Author

Nadia German