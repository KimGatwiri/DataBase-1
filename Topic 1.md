# Introduction to Databases

A **database** is an organized collection of data that allows easy access, management, and updating. Databases help store, retrieve, and manipulate data efficiently.

## Database Management System (DBMS)
A **DBMS (Database Management System)** is software that allows users to create, manage, and manipulate databases.

### Examples of DBMS:
- MySQL
- PostgreSQL
- SQLite
- MongoDB
- Microsoft SQL Server

##  Database Models
Database models define how data is structured and related within a database.

### Types of Database Models:
1. **Hierarchical Model** – Data is stored in a tree-like structure (e.g., an organization’s hierarchy).
2. **Network Model** – Similar to hierarchical but allows multiple parent-child relationships.
3. **Relational Model (RDBMS)** – Data is stored in tables with relationships (most common model).
4. **Object-Oriented Model** – Stores data in objects (used in complex applications).


## Basic Terminologies:
- **Data**: Raw facts and figures (e.g., "John", 25, "New York").
- **Record (Tuple)**: A single row in a table (e.g., one student’s details in a student table).
- **Table**: A collection of records with columns and rows.
- **Field (Attribute)**: A column in a table representing a specific data type (e.g., `Student_Name`).

### Example Table: Student Information
| Student_ID | Name   | Age | Course  |
|------------|--------|-----|---------|
| 101        | Alice  | 20  | CS      |
| 102        | Bob    | 22  | IT      |
| 103        | Carol  | 21  | AI      |

- **Table**: `Students`
- **Records (Tuples)**: Each row (e.g., Alice, Bob, Carol)
- **Fields (Attributes)**: Student_ID, Name, Age, Course

## Constraints
Constraints are rules applied to database tables to maintain accuracy and integrity of the data.

### Common Constraints:
- **Primary Key**: Uniquely identifies a record (e.g., `Student_ID`).
- **Foreign Key**: Links a table to another table (e.g., `Course_ID` in the student table referring to a course table).
- **NOT NULL**: Ensures a field cannot be empty.
- **UNIQUE**: Ensures no duplicate values in a column.
- **CHECK**: Ensures values meet a specific condition (e.g., Age > 18).

##  Relational Database Management System (RDBMS)
An **RDBMS (Relational Database Management System)** stores data in tables and establishes relationships between them.

### Examples of RDBMS:
- MySQL
- PostgreSQL
- Oracle Database
- Microsoft SQL Server

##  Relationship Types in Databases
Relationships define how tables are connected in an RDBMS.

### Types of Relationships:
1. **One-to-One (1:1)** – Each record in Table A has exactly one matching record in Table B.
2. **One-to-Many (1:M)** – A record in Table A can be linked to multiple records in Table B.
3. **Many-to-Many (M:M)** – Multiple records in Table A relate to multiple records in Table B.

### Example:
- **One-to-Many**: A teacher teaches multiple students but each student has only one teacher.
- **Many-to-Many**: Students enroll in multiple courses, and each course has multiple students.

##  Keys in Databases
Keys are used to identify and establish relationships between records.

### Types of Keys:
- **Primary Key**: Uniquely identifies a record (e.g., `Student_ID`).
- **Foreign Key**: Links to a primary key from another table.
- **Candidate Key**: A column that can be a primary key.
- **Composite Key**: A key that consists of multiple columns.
- **Surrogate Key**: A system-generated unique identifier.

### Foreign Key in Detail
A **foreign key** is a field in one table that uniquely identifies a row in another table. It ensures data consistency and maintains referential integrity.

#### Example:
Consider two tables: `Students` and `Courses`.

| Course_ID | Course_Name |
|-----------|------------|
| 201       | Computer Science |
| 202       | Information Technology |

| Student_ID | Name   | Age | Course_ID |
|------------|--------|-----|----------|
| 101        | Alice  | 20  | 201      |
| 102        | Bob    | 22  | 202      |
| 103        | Carol  | 21  | 201      |

Here:
- `Course_ID` in the `Courses` table is the **Primary Key**.
- `Course_ID` in the `Students` table is the **Foreign Key**, ensuring that every student is assigned to a valid course.

If we try to insert a student with a `Course_ID` that does not exist in the `Courses` table, the database will prevent the action to maintain referential integrity.

## Referential Integrity
Referential integrity ensures that relationships between tables remain consistent.

### Example:
If a student is enrolled in a course, referential integrity ensures that the course exists before allowing the student record to reference it.

#### Without Referential Integrity:
- A student may be assigned to a course that does not exist.

#### With Referential Integrity:
- A foreign key constraint ensures that only valid course IDs can be assigned.

---

🎓
