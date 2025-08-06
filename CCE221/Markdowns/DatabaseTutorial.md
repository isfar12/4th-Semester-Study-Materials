# What is Database?

A database is an organized collection of data that is stored and accessed electronically. It allows users to efficiently store, retrieve, manage, and manipulate information. Databases can hold various types of data — such as text, numbers, images, and even videos — and are commonly used in software systems, websites, businesses, and more.

# What is the purpose of Database?

- Efficient data storage

- Fast data retrieval

- Easy data management (create, read, update, delete)

- Ensures data integrity and accuracy

- Provides data security and access control

- Supports multi-user access (concurrency)

- Backup and recovery options

- Enables data sharing across applications

- Reduces data redundancy

- Supports decision-making through data analysis

# Some real life example of Database

Here are some **real-life example tables** used in different fields:

---

### 1. **Hospital Management System**

| **PatientID** | **Name**       | **Age** | **Diagnosis** | **DoctorAssigned** | **AdmissionDate** |
| ------------- | -------------- | ------- | ------------- | ------------------ | ----------------- |
| P001          | Ayesha Rahman  | 30      | Dengue        | Dr. Karim          | 2025-08-01        |
| P002          | Tanvir Hossain | 45      | Diabetes      | Dr. Nasrin         | 2025-08-03        |

---

### 2. **Online Shopping Website**

| **OrderID** | **CustomerName** | **Product** | **Quantity** | **Price**  | **OrderDate** |
| ----------- | ---------------- | ----------- | ------------ | ---------- | ------------- |
| O1001       | Sadia Akter      | T-shirt     | 2            | 800 BDT    | 2025-08-02    |
| O1002       | Rafiul Islam     | Laptop      | 1            | 55,000 BDT | 2025-08-04    |

---

# What is an **Entity** in a Database?

An **entity** is a real-world object or concept that can be identified and stored in a database. It represents something about which data is stored.

- Think of an **entity** as a **"thing"** — like a person, place, object, or event.
- Each entity becomes a **table** in the database.

**Examples of Entities:**

- `Student` (in a school database)
- `Product` (in an e-commerce database)
- `Employee` (in a company database)
- `Book` (in a library database)

---

# What is an **Attribute** in a Database?

An **attribute** is a piece of information or property that describes an entity. In a database, attributes are the **columns** in a table.

**Examples of Attributes:**
For the entity `Student`, possible attributes include:

- `StudentID`
- `Name`
- `Age`
- `Class`
- `GPA`

So in summary:

| Term          | Description                               | Example               |
| ------------- | ----------------------------------------- | --------------------- |
| **Entity**    | Object/table stored in database           | `Student`, `Book`     |
| **Attribute** | Property/column that describes the entity | `Name`, `GPA`, `ISBN` |

# What are the different types of attributes?

Here’s a table listing the **types of attributes** in a database, along with their descriptions and examples:

| **Attribute Type**   | **Description**                              | **Example**                          |
| -------------------- | -------------------------------------------- | ------------------------------------ |
| **Simple (Atomic)**  | Cannot be divided further                    | `Age`, `Salary`, `Name`              |
| **Composite**        | Can be divided into smaller sub-parts        | `FullName` → `FirstName`, `LastName` |
| **Derived**          | Can be derived from other attributes         | `Age` (derived from `DateOfBirth`)   |
| **Single-valued**    | Holds only one value for an entity           | `Email`, `PhoneNumber`               |
| **Multi-valued**     | Can hold multiple values for a single entity | `Skills`, `PhoneNumbers`             |
| **Key Attribute**    | Uniquely identifies an entity                | `StudentID`, `EmployeeID`            |
| **Stored Attribute** | Value is stored directly in the database     | `DateOfBirth`, `Name`                |
| **Null-valued**      | Can have a missing or unknown value          | `MiddleName` (may be empty for some) |

# What is a Key in a Database?

A **key** in a database is a **field or a set of fields** that is used to **uniquely identify rows (records)** in a table. Keys help ensure data integrity and establish relationships between tables.

---

### 📋 Types of Keys in DB (with Explanation)

| **Key Type**      | **Description**                                                                   | **Example**                                          |
| ----------------- | --------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Primary Key**   | Uniquely identifies each record in a table. Cannot be null or duplicated.         | `StudentID` in a `Students` table                    |
| **Candidate Key** | A field (or set of fields) that could be a primary key. One is chosen as primary. | `Email`, `NationalID` (only one is chosen)           |
| **Alternate Key** | A candidate key that was not selected as the primary key.                         | If `Email` is not selected, it becomes alternate key |
| **Composite Key** | A key made up of two or more columns to uniquely identify a record.               | `OrderID + ProductID` in `OrderDetails`              |
| **Foreign Key**   | A field in one table that refers to the primary key in another table.             | `CustomerID` in `Orders` (linked to `Customers`)     |
| **Unique Key**    | Ensures all values in the column are different, allows null (only once).          | `Username` in `Users` table                          |
| **Super Key**     | Any combination of columns that can uniquely identify a row.                      | `StudentID + Email`, `NationalID`                    |

---

### Summary

- **Primary Key** → Main identifier (no duplicates or nulls)
- **Foreign Key** → Creates relationships between tables
- **Composite Key** → Combination of columns as key
- **Candidate/Alternate/Super Key** → Potential identifiers
- **Unique Key** → Ensures uniqueness but allows nulls

# What is a Relationship in a Database?

A **relationship** in a database defines how **two or more tables** are logically connected based on shared data. Relationships allow databases to store data efficiently without duplication and enable meaningful data retrieval through **joins**.

Relationships are typically established using **primary keys** and **foreign keys**.

---

# What are the types of relationships in a database?

| **Relationship Type**   | **Description**                                                               | **Example**                                                                     |
| ----------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **One-to-One (1:1)**    | One record in Table A is related to only one record in Table B                | Each `person` has **one** `passport` and vice versa                             |
| **One-to-Many (1\:N)**  | One record in Table A relates to **many** records in Table B                  | One `customer` can place **many** `orders`                                      |
| **Many-to-One (N:1)**   | Many records in Table A relate to **one** record in Table B                   | Many `students` belong to **one** `department`                                  |
| **Many-to-Many (M\:N)** | Many records in Table A relate to many in Table B (via junction/bridge table) | Many `students` enroll in many `courses` (using `Enrollment` table)             |
| **Self-Referencing**    | A table has a relationship with itself                                        | An `employee` table where each employee may have a `manager` (another employee) |

---

### Summary Table

| **Type**         | **Symbolic Notation** | **Example Tables**              |
| ---------------- | --------------------- | ------------------------------- |
| One-to-One       | 1:1                   | Person — Passport               |
| One-to-Many      | 1\:N                  | Customer — Orders               |
| Many-to-One      | N:1                   | Students — Department           |
| Many-to-Many     | M\:N                  | Students — Courses              |
| Self-Referencing | Recursive             | Employee — Manager (same table) |

