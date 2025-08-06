## 💡 SCENARIO OVERVIEW: UNIVERSITY COURSE REGISTRATION SYSTEM

We will use a **Student-Course-Instructor** database for all three normal forms. The goal is to organize the data efficiently.

---

## 🔴 UNNORMALIZED FORM (UNF): Raw Table (Not in 1NF)

| StudentID | StudentName | Courses            | Instructors        |
| --------- | ----------- | ------------------ | ------------------ |
| 101       | Alice       | Math, Physics      | Dr. Ray, Dr. Stone |
| 102       | Bob         | Math               | Dr. Ray            |
| 103       | Charlie     | Physics, Chemistry | Dr. Stone, Dr. Lim |

### ❌ Issues:

* `Courses` and `Instructors` have **multiple values** in a single cell → **violates atomicity**
* Hard to search or update specific course or instructor

---

## ✅ **1st Normal Form (1NF)**: Eliminate Repeating Groups

**Rule**: Each attribute value must be **atomic** (no lists or sets).

### ✅ Convert the above table into:

| StudentID | StudentName | Course    | Instructor |
| --------- | ----------- | --------- | ---------- |
| 101       | Alice       | Math      | Dr. Ray    |
| 101       | Alice       | Physics   | Dr. Stone  |
| 102       | Bob         | Math      | Dr. Ray    |
| 103       | Charlie     | Physics   | Dr. Stone  |
| 103       | Charlie     | Chemistry | Dr. Lim    |

### 🔍 Now:

* No multiple values in any field.
* Each row = 1 piece of information.
* We’re in **1NF** ✅

---

## ✅ **2nd Normal Form (2NF)**: Remove Partial Dependencies

**Rule**: Non-key attributes should depend on the **whole composite key**, not just part of it.

**Step 1**: Identify the Composite Key
👉 Primary key = (StudentID, Course)

**Problem**:

* `StudentName` depends **only on StudentID**, not the whole composite key.

---

### 🔧 Solution: Break into 2 tables

#### A. **Students Table**

| StudentID | StudentName |
| --------- | ----------- |
| 101       | Alice       |
| 102       | Bob         |
| 103       | Charlie     |

#### B. **Enrollments Table**

| StudentID | Course    | Instructor |
| --------- | --------- | ---------- |
| 101       | Math      | Dr. Ray    |
| 101       | Physics   | Dr. Stone  |
| 102       | Math      | Dr. Ray    |
| 103       | Physics   | Dr. Stone  |
| 103       | Chemistry | Dr. Lim    |

### ✅ Now:

* Each non-key column in Enrollments depends on **both StudentID and Course**
* StudentName is stored only once → no redundancy
* We are in **2NF** ✅

---

## ✅ **3rd Normal Form (3NF)**: Remove Transitive Dependencies

**Rule**: Non-key attributes must depend **only on the primary key** — no indirect dependencies.

---

### ❗Problem:

In `Enrollments`, `Instructor` depends **on Course**, not directly on (StudentID, Course).
This is a **transitive dependency**.

---

### 🔧 Solution: Split again

#### A. **Students Table** (same as before)

| StudentID | StudentName |
| --------- | ----------- |
| 101       | Alice       |
| 102       | Bob         |
| 103       | Charlie     |

#### B. **Enrollments Table** (updated)

| StudentID | Course    |
| --------- | --------- |
| 101       | Math      |
| 101       | Physics   |
| 102       | Math      |
| 103       | Physics   |
| 103       | Chemistry |

#### C. **Courses Table**

| Course    | Instructor |
| --------- | ---------- |
| Math      | Dr. Ray    |
| Physics   | Dr. Stone  |
| Chemistry | Dr. Lim    |

### ✅ Now:

* No transitive dependency.
* `Instructor` is only dependent on `Course`, and we’ve separated that into a new table.
* Data is in **3NF** ✅

---

## 🧠 EXTRA: Summary of Dependencies

| Normal Form | Problem Fixed         | Example Dependency Removed                |
| ----------- | --------------------- | ----------------------------------------- |
| 1NF         | Repeating groups      | Course list → split into rows             |
| 2NF         | Partial dependency    | StudentName depends on only StudentID     |
| 3NF         | Transitive dependency | Instructor depends on Course, not the key |

---

## ⚠️ EDGE CASES / BONUS SCENARIOS

### Case 1: One Instructor Teaches Multiple Courses

✅ No problem in 3NF. Instructor can appear multiple times in `Courses` table.

| Course  | Instructor |
| ------- | ---------- |
| Math    | Dr. Ray    |
| Physics | Dr. Ray    |

### Case 2: Team Teaching (Multiple Instructors per Course)

This violates **1NF** again!

#### Fix:

Create a **CourseInstructor** linking table:

| Course  | Instructor |
| ------- | ---------- |
| Physics | Dr. Ray    |
| Physics | Dr. Stone  |

Then link everything cleanly. Still normalizable up to 3NF with a bit more complexity.

---

## 🔚 Conclusion

Normalization is about:

* **Reducing redundancy**
* **Improving data integrity**
* **Making updates, deletions, and queries efficient and reliable**

The **first three normal forms (1NF, 2NF, 3NF)** are usually sufficient in practice.
