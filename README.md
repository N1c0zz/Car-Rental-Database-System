# 🚗 Car Rental Database Management System

## 📋 Project Overview
This project consists of the complete design and implementation of a Relational Database for a car rental company, coupled with a Java-based desktop client application. 

The system manages the entire business logic: vehicle fleet inventory, customer registrations, complex reservations (handling overlapping dates and multiple vehicles), billing, and penalty tracking.

---

## 🏗️ Tech Stack
* **Database Engine:** MySQL / MariaDB
* **Application Logic & UI:** Native Java
* **Database Connector:** JDBC (Java Database Connectivity)

---

## 🗄️ Database Engineering & Methodology
The core value of this project lies in the rigorous database design methodology applied before writing any code, which is detailed in the project's documentation.

### 1. Conceptual & Logical Design
* **Entity-Relationship (ER) Modeling:** Designed a robust conceptual schema managing inheritance (e.g., generalized `Persona` into `Cliente` and `Impiegato`) and complex constraints (e.g., maximum 2 vehicles per reservation in the same timeframe).
* **Logical Translation:** Mapped the ER diagram to a normalized Relational Schema, resolving many-to-many relationships and flattening hierarchies for optimal read performance.

### 2. Performance Optimization & Redundancy Analysis
Instead of blind normalization, the schema was optimized based on **Access Cost Estimation (Volume/Frequency analysis)**. 
For example, the decision to maintain redundant data (like the total number of rentals per user) was mathematically justified by comparing the I/O cost of reading a cached attribute versus computing a `COUNT()` via complex `JOIN` operations on a large scale.

### 3. ACID Transactions (JDBC)
To ensure data integrity (e.g., when a reservation is created, vehicles are locked, and billing is generated), the Java application implements strict **Transaction Management**. Complex SQL operations are grouped using JDBC `Commit` and `Rollback` commands, ensuring Atomicity and preventing partial data writes in case of runtime errors.

---

## 🚀 Getting Started

The application is provided with a pre-compiled Windows executable, but it requires a local MySQL database to function.

### Prerequisites
* MySQL Server (e.g., via XAMPP or native installation)
* Java Runtime Environment (JRE)
* Windows OS (for the `.exe` client)

### Database Setup
1. Clone this repository:
   ```bash
   git clone https://github.com/N1c0zz/Car-Rental-Database-System.git
   ```
2. Open your MySQL client (e.g., MySQL Workbench, phpMyAdmin).
3. Create a new schema (e.g., `noleggio_auto`).
4. Import the provided SQL dump file (containing table structures and triggers) into your local database.
5. *Note: Ensure your local MySQL server accepts connections on the default port `3306` with the credentials expected by the Java app.*

### Running the Application
1. Navigate to the root directory of the repository.
2. Run the `AppNoleggio.exe` file.
3. Use the following default credentials to access the system:
   * **Username:** `Admin`
   * **Password:** `password`

*(Tip: Press `ESC` at any time to exit the fullscreen mode).*

---
*Developed by Nicolò Morini*
