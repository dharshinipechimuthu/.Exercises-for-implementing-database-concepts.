# .Exercises-for-implementing-database-concepts.
CREATE DATABASE COLLEGE_DB;
Database created.
USE COLLEGE_DB;
Database changed.
CREATE TABLE STUDENT (
    Roll_No INT PRIMARY KEY,
    Name VARCHAR(30) NOT NULL,
    Age INT,
    Department VARCHAR(20)
);
Table created.
CREATE TABLE COURSE (
    Course_ID INT PRIMARY KEY,
    Course_Name VARCHAR(30),
    Credits INT
);
Table created.
INSERT INTO STUDENT VALUES
(1, 'Rahul', 20, 'CSE'),
(2, 'Anita', 21, 'ECE'),
(3, 'Suresh', 22, 'ME');
3 rows inserted.
INSERT INTO COURSE VALUES
(101, 'DBMS', 4),
(102, 'OS', 3);
2 rows inserted.
SELECT * FROM STUDENT;
+---------+--------+-----+------------+
| Roll_No | Name   | Age | Department |
+---------+--------+-----+------------+
| 1       | Rahul  | 20  | CSE        |
| 2       | Anita  | 21  | ECE        |
| 3       | Suresh | 22  | ME         |
+---------+--------+-----+------------+
UPDATE STUDENT
SET Department = 'CSE'
WHERE Roll_No = 2;
1 row updated.
1 row updated.
DELETE FROM STUDENT
WHERE Roll_No = 3;
1 row deleted.
SELECT COUNT(*) AS Total_Students FROM STUDENT;
CREATE TABLE ENROLLMENT (
    Roll_No INT,
    Course_ID INT,
    FOREIGN KEY (Roll_No) REFERENCES STUDENT(Roll_No),
    FOREIGN KEY (Course_ID) REFERENCES COURSE(Course_ID)
);
Table created.
SELECT STUDENT.Name, COURSE.Course_Name
FROM STUDENT
JOIN ENROLLMENT ON STUDENT.Roll_No = ENROLLMENT.Roll_No
JOIN COURSE ON COURSE.Course_ID = ENROLLMENT.Course_ID;
+-------+-------------+
| Name  | Course_Name |
+-------+-------------+
| Rahul | DBMS        |
+-------+-------------+
