# Simple Banking Application with CRUD Operations

A Java Swing desktop application designed to manage bank customer profiles, open multi-tier accounts, perform real-time transactions, and record historical log traces securely using a MySQL backend engine.

Developed as a laboratory requirement for Engineering Mathematics and Structured Data Management applications.

---

## 📌 System Description

The Simple Banking Application functions as an automated bank accounting system. It consolidates two core domains of a retail bank: **Account Management** and **Transaction Processing**. 

Through a centralized interface dashboard, users can perform the following:
* **Customer Registry:** Add new client profiles into the system.
* **Account Provisioning:** Open accounts (Savings or Current) with initial balance fields.
* **Full CRUD Pipeline:** Read real-time accounts on a data table, edit profile names, and delete/close closed entries.
* **Dynamic Search engine:** Filter the active database instantly by typing customer names or direct Account IDs.
* **Transaction Engine:** Run Deposits and Withdrawals that instantly update account balances while rejecting overdraft attempts with "Insufficient Balance" warning panels.
* **Audit Logs:** View a chronological database window of all historical actions executed across the system.

---

## 📊 ERD Explanation & Structural Relationships

The system relies on a relational database architecture composed of three normalized tables. The layout maps out strict structural dependencies to ensure information consistency:



### 1. Entity Definitions
* **Customer Table:** Stores unique personal identity keys (`customer_id` [Primary Key], `first_name`, `last_name`, `email`, `phone_number`).
* **Account Table:** Manages financial asset balances (`account_id` [Primary Key], `customer_id` [Foreign Key], `account_type`, `balance`).
* **Transaction Table:** Logs ledger changes sequentially (`transaction_id` [Primary Key], `account_id` [Foreign Key], `transaction_type`, `amount`, `transaction_date`).

### 2. Relationship Cardinality
* **One Customer → Many Accounts:** A single customer profile can own multiple separate bank accounts (e.g., matching both a Savings and a Current account string). However, every account records an identity loop back to exactly one primary customer key.
* **One Account → Many Transactions:** A single bank account can accumulate an endless list of historical deposit or withdrawal entries over time. Every transaction record links back directly to the parent account that initiated the move.

> ⚠️ **Database Guardrail:** Tables are established using `ON DELETE CASCADE` constraints. If an account is dropped from the registry, its entire transactional history record is wiped simultaneously to maintain system efficiency.

---

## 💻 How to Run the Program

Follow these steps to deploy and run the application on your local workspace environment:

### Prerequisites
1. **Java Development Kit (JDK):** Version 11 or higher installed.
2. **IDE:** Apache NetBeans (Version 12 or above).
3. **Database:** Standalone MySQL Server Instance running on port `3306`.

### Step 1: Database Construction
1. Open your database management panel (**MySQL Workbench**).
2. Create a new SQL query tab, paste your database schema script, and execute it.
3. Confirm that the `banking_db` schema is active alongside its three tables (`Customer`, `Account`, `Transaction`).

### Step 2: Open Project in Apache NetBeans
1. Launch **Apache NetBeans**.
2. Navigate to **File > Open Project...**
3. Select the root directory folder named `BankingSystemCRUD_LastName_FirstName` and click **Open**.

### Step 3: Configure Database Credentials
1. Expand your source files, navigate to the `config` package, and open `DatabaseConnection.java`.
2. Edit the connection string constants to match your personal MySQL setup:
   ```java
   private static final String URL = "jdbc:mysql://localhost:3306/banking_db";
   private static final String USER = "root";
   private static final String PASSWORD = "YOUR_PERSONAL_MYSQL_PASSWORD";
