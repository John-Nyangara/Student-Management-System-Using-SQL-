# Student-Management-System-Using-SQL-
This project involves basic ddl dml and dcl commands in sql through managing records in a school environment 

Dataset Overview
The Student Management System consists of five main tables. These tables are connected using primary and foreign keys.

Table	Description
students	Stores student details
courses	Stores available course details
teachers	Stores teacher information
enrollments	Connects students with their courses
marks	Stores marks obtained by students
Below are the steps to build and manage the Student Management System using SQL table operations.

**Step 1: Create the Student Management Tables**
First, create the database and required tables using the CREATE DATABASE and CREATE TABLE statements. Primary and foreign keys are used to establish relationships between the tables.

CREATE TABLE students (
    student_id INT PRIMARY KEY,
    student_name VARCHAR(100),
    email VARCHAR(150),
    admission_year INT
);

CREATE TABLE teachers (
    teacher_id INT PRIMARY KEY,
    teacher_name VARCHAR(100),
    department VARCHAR(100)
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY,
    course_name VARCHAR(100),
    teacher_id INT,
    FOREIGN KEY (teacher_id)
        REFERENCES teachers(teacher_id)
);

CREATE TABLE enrollments (
    enrollment_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    enrollment_date DATE,
    FOREIGN KEY (student_id)
        REFERENCES students(student_id),
    FOREIGN KEY (course_id)
        REFERENCES courses(course_id)
);

CREATE TABLE marks (
    mark_id INT PRIMARY KEY,
    student_id INT,
    course_id INT,
    marks_obtained INT,
    FOREIGN KEY (student_id)
        REFERENCES students(student_id),
    FOREIGN KEY (course_id)
        REFERENCES courses(course_id)
);

**Database schema**
<img width="349" height="132" alt="DB description " src="https://github.com/user-attachments/assets/e23e6cef-3813-41b4-8e89-f28b46d662bd" />

**Er diagram**

<img width="674" height="510" alt="relationship diagram" src="https://github.com/user-attachments/assets/9dc4185f-9e55-4153-af9a-0cd27ba9a87a" />

**Step 2: Add Contact Information to Students**
Suppose the institution decides to maintain the phone number of every student. Instead of recreating the students table, we can modify it using ALTER TABLE.

ALTER TABLE students
ADD COLUMN phone VARCHAR(15);

<img width="950" height="202" alt="Screenshot 2026-11-18 145420" src="https://github.com/user-attachments/assets/6de8bdb7-2964-4249-9ca1-97e3bcfc0d7d" />

**Step 3: Rename the Marks Table**
Suppose the institution wants to use a more descriptive name for the marks table.

ALTER TABLE marks
RENAME TO student_marks;
This renames the marks table to student_marks while retaining its table structure.

**Step 4: Create a Copy of the Students Table**
Before making major structural changes, the institution may create a copy of the students table.
CREATE TABLE students_backup AS SELECT * FROM students;

**Step 5: Drop Backup Table**
Once the backup is no longer required, it can be permanently removed from the 
database.DROP TABLE students_backup;

We can check whether the `students_backup` table exists using the following 
query.SELECT * FROM students_backup;


