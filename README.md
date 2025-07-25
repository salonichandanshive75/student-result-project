# student-result-project
 Objective:
To design and implement a database system in MySQL that can manage student academic records, calculate GPA/CGPA, determine pass/fail status, and generate rank lists.

🔹 Tools Used:
Database: MySQL Workbench

Language: SQL

🔹 Database Schema:
Students: Stores student details

Courses: Stores course information and credit value

Semesters: Records semester information

Grades: Links students to their course grades

🔹 Features Implemented:
Schema Design for Students, Courses, Semesters, and Grades.

Data Insertion for sample students, courses, and marks.

GPA Calculation using weighted grade points.

Pass/Fail Report using conditional aggregation.

Rank List using SQL RANK() window function.

Triggers (optional) for automated GPA updates.

Exportable Result Summary semester-wise from query result.

🔹 Sample Queries:
GPA Calculation:

SELECT s.name, 
       SUM(CASE grade 
            WHEN 'A' THEN 10 
            WHEN 'B' THEN 8 
            WHEN 'C' THEN 6 
            WHEN 'D' THEN 4 
            ELSE 0 
          END * c.credits) / SUM(c.credits) AS GPA
FROM Grades g
JOIN Students s ON g.student_id = s.student_id
JOIN Courses c ON g.course_id = c.course_id
GROUP BY s.student_id;
Rank List:

SELECT s.name, 
       RANK() OVER (ORDER BY SUM(CASE grade WHEN 'A' THEN 10 ... END * credits) / SUM(credits) DESC) AS Rank
FROM
Exporting:

🔹 Outcome:
The system enables seamless tracking of student performance, supports academic reporting, and can be expanded for use in school/college result management.
