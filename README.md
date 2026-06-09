# Banking System CRUD Application

This application is a desktop banking system built using Java Swing for the graphical interface and MySQL for the database backend. It allows users to manage customer accounts, process deposits and withdrawals, and view transaction history logs.

---

## System Description

The system acts as a digital portal for bank operators to manage core data operations. It is split into three functional modules:

* **Account Management:** Allows creation of new client records along with their initial account setups. Existing entries can be updated or permanently deleted. A built-in search function filters table records by customer name or account ID.
* **Transactions:** Processes deposits and withdrawals. It automatically reads the current balance from the database, runs mathematical calculations, and blocks withdrawals if the account does not have enough money.
* **Logs:** Displays a master spreadsheet tracking every financial activity with exact transaction details and timestamps.

---

## Database Schema and Relationships

The database structure consists of three normalized tables to maintain data integrity.

* **Customer Table:** Stores personal data (`customer_id`, `first_name`, `last_name`, `email`, `phone_number`).
* **Account Table:** Stores financial balances (`account_id`, `customer_id`, `account_type`, `balance`).
* **Transaction Table:** Stores ledger history records (`transaction_id`, `account_id`, `transaction_type`, `amount`, `transaction_date`).

### Relationships
* **One Customer to Many Accounts:** A single customer record can be linked to multiple bank accounts, but each account can belong to only one customer.
* **One Account to Many Transactions:** A single bank account can accumulate multiple historical transaction records over time.

Foreign keys use `ON DELETE CASCADE` constraints. If a customer or account record is deleted, all corresponding logs and balances are automatically removed to prevent orphaned data.

---

## How to Run the Program

### Prerequisites
* Java Development Kit (JDK) installed.
* Apache NetBeans IDE.
* MySQL Server instance active on your local computer.

### Step 1: Initialize the Database
1. Open your MySQL client (such as MySQL Workbench).
2. Create
