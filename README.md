# Banking System CRUD Application

An intuitive Java Swing desktop application designed for streamlined bank customer management, account creation, and secure transaction logging. This system implements full CRUD operations, conditional transaction validations, and real-world relational database architectures using a MySQL backend engine.

Developed as a standard academic laboratory project for Engineering Mathematics and Structured Programming applications.

---

## 📌 Features

### 1. Customer & Account Management
* **Create (Add):** Dynamically registers new bank customer profiles and opens a corresponding bank account (Savings or Current) under a unified transaction block.
* **Read (View):** Displays comprehensive multi-table account and profile data sets dynamically on a structured interface spreadsheet.
* **Update:** Modifies active customer profile parameters and account classifications seamlessly.
* **Delete:** Closes active accounts and cleans up linked profile traces using cascading database rules.
* **Search Infrastructure:** Filters complex dataset registers instantly by parsing Customer Names or unique Account IDs.

### 2. Transaction Processing Hub
* **Deposits:** Multiplies active account ledger assets securely with automated mathematical state balances.
* **Withdrawals:** Validates financial constraints instantly, preventing account overdraft operations via programmatic asset balance evaluations.
* **Historical Audits:** Logs chronological transaction records permanently into data storage structures.

---

## 🛠️ Database Design & ERD Explanation

The application relies on a **One-to-Many (1:N)** relational architecture mapped across three main normalized entities:

1. **Customer Table:** Holds structural identity metadata (`customer_id` [PK], `first_name`, `last_name`, `email`, `phone_number`).
2. **Account Table:** Tracks specific bank holdings (`account_id` [PK], `customer_id` [FK], `account_type`, `balance`). 
   * *Relationship:* One Customer can own multiple distinct Bank Accounts (**One-to-Many**).
3. **Transaction Table:** Archives chronological account activities (`transaction_id` [PK], `account_id` [FK], `transaction_type`, `amount`, `transaction_date`).
   * *Relationship:* One Account can generate an infinite array of historical logs (**One-to-Many**).

> ⚠️ **Data Integrity Safeguard:** Tables are linked using `ON DELETE CASCADE` rules. Removing an account automatically purges associated transactional records, preventing orphaned database links.

---

## 💻 How to Setup and Run

### Prerequisites
* **Java Development Kit (JDK):** Version 11 or higher.
* **IDE:** Apache NetBeans (Version 12+ recommended).
* **Database Engine:** MySQL Server Instance (Standalone installer or via XAMPP).

### Step 1: Database Setup
1. Launch your MySQL Server administration tool (e.g., **MySQL Workbench**).
2. Open a new SQL script tab, paste the setup script found inside your database configuration file, and execute it.
3. Verify that `banking_db` is compiled successfully along with its 3 tables (`Customer`, `Account`, `Transaction`).

### Step 2: Open Project in Apache NetBeans
1. Open **Apache NetBeans**.
2. Click **File > Open Project...**
3. Navigate to the directory where this repository was cloned and select `BankingSystemCRUD_LastName_FirstName`.

### Step 3: Configure Database Credentials
1. Navigate to the `config` package and open `DatabaseConnection.java`.
2. Modify the `PASSWORD` string constant to match your local MySQL configuration password:
   ```java
   private static final String PASSWORD = "YOUR_ACTUAL_DATABASE_PASSWORD";
