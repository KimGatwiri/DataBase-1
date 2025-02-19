# Database Normalization

## 📌 Definitions
Database normalization is the process of **organizing a relational database** to reduce **redundancy** and improve **data integrity**. It involves **structuring tables** according to specific rules (normal forms) to minimize duplicate data and dependency issues.

Normalization typically follows a step-by-step process, moving through different **normal forms (NF)** to achieve an optimized database design.

## 📌 Characteristics of a Normalized Database
A **well-normalized database** should:
- **Eliminate redundancy** (no unnecessary duplicate data)
-  **Ensure data integrity** (reduce inconsistency)
- **Simplify queries** (reduce complexity in data retrieval)
-  **Minimize update anomalies** (changes in one place should not require multiple modifications)
- **Use efficient storage** (avoiding unnecessary data repetition)

## 📌 Unnormalized Form (UNF)
A **database is in UNF** if it contains **repeating groups** or **multivalued attributes**. This means that data is stored in a way that allows multiple values within a single column.

### 🔹 Example of UNF Table:
| Order ID | Customer Name | Product Name |
|----------|--------------|--------------|
| 101      | Alice        | Laptop, Mouse |
| 102      | Bob          | Keyboard     |
| 103      | Charlie      | Monitor, Mouse |

### 🔹 Problems with UNF:
- ❌ **Repeating values** within a single column (e.g., multiple products in one row)
- ❌ **Difficult to query** individual items
- ❌ **Leads to anomalies** (insertion, deletion, update issues)

## 📌 First Normal Form (1NF) - Eliminate Repeating Groups
A table is in **1NF** if:
 All columns contain **atomic values** (single values per field)
Each column contains **values of the same type**
There is a **unique identifier (Primary Key)**

### 🔹 Example of 1NF Table:
| Order ID | Customer Name | Product Name  |
|----------|--------------|--------------|
| 101      | Alice        | Laptop       |
| 101      | Alice        | Mouse        |
| 102      | Bob          | Keyboard     |
| 103      | Charlie      | Monitor      |
| 103      | Charlie      | Mouse        |

Now, **each row contains a single atomic value**, making it easier to query.

## 📌 Second Normal Form (2NF) - Remove Partial Dependencies
A table is in **2NF** if:
It is already in **1NF**
 **All non-key attributes** are **fully dependent** on the entire **Primary Key** (no partial dependencies)

### 🔹 Example: Before 2NF
| Order ID | Customer Name | Product ID | Product Name |
|----------|--------------|------------|--------------|
| 101      | Alice        | P1         | Laptop       |
| 101      | Alice        | P2         | Mouse        |
| 102      | Bob          | P3         | Keyboard     |

Here, **Customer Name** depends only on **Order ID**, not on the entire composite key (`Order ID`, `Product ID`).

### 🔹 Fixing to 2NF (Splitting Tables):
#### **Orders Table**
| Order ID | Customer Name |
|----------|--------------|
| 101      | Alice        |
| 102      | Bob          |

#### **Order Details Table**
| Order ID | Product ID |
|----------|------------|
| 101      | P1         |
| 101      | P2         |
| 102      | P3         |

#### **Products Table**
| Product ID | Product Name |
|------------|--------------|
| P1         | Laptop       |
| P2         | Mouse        |
| P3         | Keyboard     |

Now, **each non-key column depends on the whole Primary Key**, eliminating partial dependency.

##  Third Normal Form (3NF) - Remove Transitive Dependencies
A table is in **3NF** if:
t is already in **2NF**
**No non-key attribute depends on another non-key attribute** (transitive dependency)

### 🔹 Example: Before 3NF
| Order ID | Customer ID | Customer Name | Product ID | Product Name |
|----------|------------|--------------|------------|--------------|
| 101      | C1         | Alice        | P1         | Laptop       |
| 102      | C2         | Bob          | P3         | Keyboard     |

Here, **Customer Name** depends on **Customer ID**, and **Product Name** depends on **Product ID** (transitive dependencies).

### 🔹 Fixing to 3NF (Splitting Tables):
#### **Orders Table**
| Order ID | Customer ID |
|----------|------------|
| 101      | C1         |
| 102      | C2         |

#### **Customers Table**
| Customer ID | Customer Name |
|------------|--------------|
| C1         | Alice        |
| C2         | Bob          |

#### **Order Details Table**
| Order ID | Product ID |
|----------|------------|
| 101      | P1         |
| 102      | P3         |

#### **Products Table**
| Product ID | Product Name |
|------------|--------------|
| P1         | Laptop       |
| P3         | Keyboard     |

Now, all **non-key attributes** depend **only on the primary key**, removing transitive dependencies.

---
## **📌 Summary of Normal Forms**
| Normal Form | Key Rule |
|-------------|---------|
| UNF | Data is unstructured with repeating groups |
| 1NF | Eliminate repeating groups & ensure atomic values |
| 2NF | Remove partial dependencies (non-key attributes depend on full PK) |
| 3NF | Remove transitive dependencies (non-key attributes depend only on PK) |

---
## ** Why Normalize?**
**Prevents redundancy** & saves space
**Improves consistency** by avoiding duplicate data
**Ensures data integrity** and avoids update anomalies
**Makes queries more efficient** and structured
**Easier to maintain & scale** in large databases

---
## ** Next Steps**
Beyond **3NF**, there are **higher normal forms** like **BCNF (Boyce-Codd Normal Form), 4NF, and 5NF**, but these are usually needed for more complex databases.

---
