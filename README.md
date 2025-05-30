# PSQL Assignment

# Creating students table:
```js
university_db=> CREATE TABLE students (
university_db(> student_id INTEGER,
university_db(> first_name VARCHAR(50),
university_db(> last_name VARCHAR(50),
university_db(> email VARCHAR(100),
university_db(> date_of_birth DATE
university_db(> );
CREATE TABLE

university_db=> \d
         List of relations
 Schema |   Name   | Type  | Owner
--------+----------+-------+--------
 public | students | table | avi600
(1 row)
```
# ALTER TABLE Statement:
```js
university_db=> ALTER TABLE students ADD COLUMN enrollment_date DATE;
ALTER TABLE
university_db=> ALTER TABLE students DROP COLUMN enrollment_date;
ALTER TABLE              
university_db=> ALTER TABLE students ALTER COLUMN email TYPE VARCHAR(150);
ALTER TABLE
university_db=> ALTER TABLE students RENAME COLUMN date_of_birth TO dob;
ALTER TABLE
university_db=> ALTER TABLE students ADD CONSTRAINT unique_email UNIQUE (email);
ALTER TABLE
```
# Activity adding phone_number column and then droping:
```js
university_db=>  ALTER TABLE students ADD COLUMN phone_number VARCHAR(20);
ALTER TABLE
university_db=>  ALTER TABLE students DROP COLUMN phone_number;
ALTER TABLE
```
# Adding Data to Tables:
```js
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob)
university_db-> VALUES (2, 'Bob', 'Johnson', 'bob.johnson@example.com', '2002-08-22'),
university_db->        (3, 'Charlie', 'Brown', 'charlie.brown@example.com', '2003-01-10');
INSERT 0 2
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob) VALUES (1, 'Alice', 'Smith', 'alice.smith@example.com', '2003-05-15');
INSERT 0 1
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob) VALUES (4, 'rohan', 'Smith', 'rohan.smith@example.com', '2008-05-18');
INSERT 0 1
university_db=>  INSERT INTO students (student_id, first_name, last_name, email, dob) VALUES (5, 'kowshik', 'Smith', 'kowshik.smith@example.com', '2008-09-19');
INSERT 0 1

university_db=> select * from students;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          2 | Bob        | Johnson   | bob.johnson@example.com   | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          5 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
(5 rows)
```
# Inserting data with Null value:
```js
university_db=>  INSERT INTO students (student_id, first_name, last_name, dob) VALUES (5, 'Aviraj', 'patil', '2006-12-12');
INSERT 0 1

university_db=> SELECT * FROM students WHERE email IS NULL;
 student_id | first_name | last_name | email |    dob
------------+------------+-----------+-------+------------
          5 | Aviraj     | patil     |       | 2006-12-12
(1 row)
```
# Activity
# Find the student with student_id 2.33:
```js
university_db=> SELECT * FROM students WHERE student_id=2.33;
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)
```
# Find all students born before January 1st, 2003:
```js
university_db=> SELECT * FROM students WHERE dob <= '2003-01-01';
 student_id | first_name | last_name |          email          |    dob
------------+------------+-----------+-------------------------+-----------
          2 | Bob        | Johnson   | bob.johnson@example.com | 2002-08-22
(1 row)
```
# Find students whose first name starts with 'B' or 'C':
```js
university_db=> SELECT * FROM students WHERE first_name LIKE 'B%' OR first_name LIKE 'C%';
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          2 | Bob        | Johnson   | bob.johnson@example.com   | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
(2 rows)
```
# Find students whose email address is from example.com:
```js
university_db=> SELECT * FROM students WHERE email ILIKE 'example.com';
 student_id | first_name | last_name | email | dob
------------+------------+-----------+-------+-----
(0 rows)
```
# Find students who do not have an email address listed:
```js
university_db=> SELECT * FROM students WHERE email IS NULL;
 student_id | first_name | last_name | email |    dob
------------+------------+-----------+-------+------------
          5 | Aviraj     | patil     |       | 2006-12-12
(1 row)
```
# Updating the Email:
```js
university_db=> UPDATE students
university_db-> SET email = 'okay@gmail.com'
university_db-> WHERE student_id = 2;
UPDATE 1
university_db=> SELECT * FROM STUDENTS;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          5 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
          5 | Aviraj     | patil     |                           | 2006-12-
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
(6 rows)
```
```js
university_db=> UPDATE students
university_db-> SET student_id = '6'
university_db-> WHERE first_name = 'kowshik';
UPDATE 1
university_db=> SELECT * FROM STUDENTS;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          6 | Aviraj     | patil     |                           | 2006-12-
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
(6 rows)
```
# Command for Asending order Last_name:
```js
university_db=> SELECT * FROM students ORDER BY last_name ASC;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          5 | Aviraj     | patil     |                           | 2006-12-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
(6 rows)
```
# Activity
# List all students ordered by their date of birth, oldest first:
```js
university_db=> SELECT * FROM students ORDER BY dob ASC;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          5 | Aviraj     | patil     |                           | 2006-12-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
(6 rows)
```
# List all students ordered by last name descending, then by first name ascending:
```js
university_db=> SELECT * FROM students ORDER BY last_name DESC;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
          5 | Aviraj     | patil     |                           | 2006-12-
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
(6 rows)

university_db=> SELECT * FROM students ORDER BY first_name ASC;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
          5 | Aviraj     | patil     |                           | 2006-12-
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-
(6 rows)
```
# Activity
# Find the two students who were born earliest (oldest two):
```js
 university_db=> SELECT * FROM students ORDER BY dob ASC LIMIT 2;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
(2 rows)
```
# List students, skipping the first one and showing the next two, ordered by student_id:
```js
university_db=> SELECT * FROM students ORDER BY dob ASC LIMIT 2 OFFSET 1;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-
(2 rows)

university_db=> SELECT * FROM students ORDER BY student_id LIMIT 2 OFFSET 1;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+---------
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-
(2 rows)

university_db=> SELECT DISTINCT last_name FROM students ORDER BY last_name;
 last_name
-----------
 Brown
 Johnson
 patil
 Smith
(4 rows)


university_db=> SELECT DISTINCT last_name, first_name FROM students;
 last_name | first_name
-----------+------------
 Smith     | kowshik
 Smith     | rohan
 Smith     | Alice
 Brown     | Charlie
 Johnson   | Bob
 patil     | Aviraj
(6 rows)


university_db=> SELECT COUNT(*) AS total_students FROM students
university_db-> ;
 total_students
----------------
              6
(1 row)


university_db=> SELECT COUNT(email) AS students_with_email FROM students;
 students_with_email
---------------------
                   5
(1 row)


university_db=> select * from students;
 student_id | first_name | last_name |           email           |    dob
------------+------------+-----------+---------------------------+------------
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-15
          4 | rohan      | Smith     | rohan.smith@example.com   | 2008-05-18
          2 | Bob        | Johnson   | okay@gmail.com            | 2002-08-22
          6 | kowshik    | Smith     | kowshik.smith@example.com | 2008-09-19
          5 | Aviraj     | patil     |                           | 2006-12-12
(6 rows)


university_db=> SELECT DISTINCT last_name FROM students;
 last_name
-----------
 patil
 Smith
 Johnson
 Brown
(4 rows)


university_db=> SELECT DISTINCT first_name FROM students;
 first_name
------------
 Alice
 Bob
 Charlie
 rohan
 kowshik
 Aviraj
(6 rows)


university_db=> SELECT EXTRACT(YEAR FROM dob) AS birth_year, COUNT(*) AS students_in_year
university_db-> FROM students
university_db-> WHERE dob IS NOT NULL
university_db-> GROUP BY birth_year
university_db-> ORDER BY birth_year;
 birth_year | students_in_year
------------+------------------
       2002 |                1
       2003 |                2
       2006 |                1
       2008 |                2
(4 rows)

```
# List students, skipping the first one and showing the next two, ordered by student_id:
```js
university_db=> DROP TABLE students;
DROP TABLE
university_db=> CREATE TABLE students (
university_db(>     student_id INTEGER,
university_db(>     first_name VARCHAR(50) NOT NULL,
university_db(>     last_name VARCHAR(50) NOT NULL,
university_db(>     email VARCHAR(100) UNIQUE,
university_db(>     dob DATE,
university_db(>     enrollment_status VARCHAR(10) CHECK (enrollment_status IN ('enrolled', 'graduated', 'dropped'))
university_db(> );
CREATE TABLE
university_db=> INSERT INTO students (student_id, last_name, email, dob) VALUES (1, 'Test', 'test@test.com', '2000-01-01'); -- Fails (first_name is NULL)
ERROR:  null value in column "first_name" of relation "students" violates not-null constraint
DETAIL:  Failing row contains (1, null, Test, test@test.com, 2000-01-01, null).
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob) VALUES (1, 'Test', 'User', 'test@test.com', '2000-01-01');
INSERT 0 1
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob) VALUES (2, 'Another', 'User', 'test@test.com', '2001-01-01');
ERROR:  duplicate key value violates unique constraint "students_email_key"
DETAIL:  Key (email)=(test@test.com) already exists.
university_db=> INSERT INTO students (student_id, first_name, last_name, email, dob, enrollment_status) VALUES (2, 'Another', 'User', 'another@test.com', '2001-01-01', 'pending');
ERROR:  new row for relation "students" violates check constraint "students_enrollment_status_check"
DETAIL:  Failing row contains (2, Another, User, another@test.com, 2001-01-01, pending).
```
# Students table with a proper Primary Key:
```js
 university_db=> DROP TABLE students;
DROP TABLE                                     
university_db=> CREATE TABLE students(
university_db(> student_id SERIAL PRIMARY KEY,
university_db(> first_name VARCHAR(50) NOT NULL,
university_db(> last_name VARCHAR(50) NOT NULL,
university_db(> email VARCHAR(100) UNIQUE,
university_db(> dob DATE,
university_db(> enrollment_status VARCHAR(20) CHECK (enrollment_status IN('enrolled','graduated', 'dropped', 'pending'))
university_db(> );
CREATE TABLE
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Alice', 'Smith', 'alice.smith@example.com', '2003-05-15', 'enrolled');
INSERT 0 1
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Robert', 'Johnson', 'robert.j@example.com', '2002-08-22', 'enrolled');
INSERT 0 1
university_db=> INSERT INTO students (first_name, last_name, email, dob, enrollment_status)
university_db-> VALUES ('Charlie', 'Brown', 'charlie.brown@example.com', '2003-01-10', 'pending');
INSERT 0 1
university_db=> SELECT * FROM students;
 student_id | first_name | last_name |           email           |    dob     | enrollment_status
------------+------------+-----------+---------------------------+------------+-------------------
          1 | Alice      | Smith     | alice.smith@example.com   | 2003-05-15 | enrolled
          2 | Robert     | Johnson   | robert.j@example.com      | 2002-08-22 | enrolled
          3 | Charlie    | Brown     | charlie.brown@example.com | 2003-01-10 | pending
(3 rows)
```
# Activity
# Creating Tables for a Many-to-Many Relationship (Students and Courses):
```js
university_db=> CREATE TABLE courses (
university_db(>     course_id SERIAL PRIMARY KEY,
university_db(>     course_name VARCHAR(100) NOT NULL UNIQUE,
university_db(>     credits INTEGER CHECK (credits > 0 AND credits < 10)
university_db(> )
university_db-> ;
CREATE TABLE
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Introduction to SQL', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Database Design', 4);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Web Development', 3);
INSERT 0 1
university_db=> INSERT INTO courses (course_name, credits) VALUES ('Data Structures', 4);
INSERT 0 1

university_db=> CREATE TABLE enrollments (
university_db(>     enrollment_id SERIAL PRIMARY KEY,
university_db(>     student_id INTEGER NOT NULL,
university_db(>     course_id INTEGER NOT NULL,
university_db(>     enrollment_date DATE DEFAULT CURRENT_DATE,
university_db(>   grade CHAR(1) CHECK (grade IN ('A', 'B', 'C', 'D', 'F', 'W', NULL)),
university_db(> CONSTRAINT fk_student
university_db(>         FOREIGN KEY (student_id)
university_db(>         REFERENCES students(student_id)
university_db(>         ON DELETE CASCADE,
university_db(> CONSTRAINT fk_course
university_db(>         FOREIGN KEY (course_id)
university_db(>         REFERENCES courses(course_id)
university_db(>         ON DELETE RESTRICT,
university_db(>  UNIQUE (student_id, course_id)
university_db(> );
CREATE TABLE
university_db=>
 ```
