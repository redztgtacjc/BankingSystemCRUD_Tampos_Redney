# 🏦 Simple Banking Application

A clean, easy-to-use desktop banking application built using Java Swing (for the visual windows) and MySQL (to save the data). This system allows bank staff to manage customer profiles, open savings or current accounts, make deposits/withdrawals, and review historical activity logs.

---

## 👀 What This System Does (System Description)

Think of this app as a digital teller dashboard. It connects two main tasks: keeping track of who your customers are, and processing their money securely.

Here is what you can do with it:
* **Create New Accounts:** Type in a customer's name, email, phone number, choose an account type (Savings or Current), and set a starting balance.
* **View & Edit profiles:** All active accounts appear on a big spreadsheet grid. If a customer changes their phone number or name, you can click their row, fix the info, and save it instantly.
* **Delete / Close Accounts:** If someone wants to close their account, you select it and hit delete. It wipes their data cleanly so no ghost profiles stay in the system.
* **Smart Search Bar:** Instead of scrolling through hundreds of names, you can type a customer’s name or their Account ID into the search bar to filter the list instantly.
* **Deposit & Withdraw Cash:** Switch to the transaction window, enter an Account ID, and add or subtract money. 
* **Safety Controls:** If a customer has ₱5,000 in their account and tries to withdraw ₱10,000, the system automatically blocks the move and shows an "Insufficient Balance" warning popup.
* **Transaction Ledger:** Every single deposit and withdrawal is logged with an exact timestamp so you can track where the money went.

---

## 📊 How the Database is Structured (ERD Explanation)

The database behind this app uses three simple tables that link together like pieces of a puzzle. 



* **Customer Table:** Stores the human details (First Name, Last Name, Email, Phone).
* **Account Table:** Stores the money details (Account ID, Account Type, Balance). It links to the Customer table because an account needs an owner. One customer can open multiple accounts (like a Savings account *and* a Current account).
* **Transaction Table:** Stores the movement history (Transaction ID, Type, Amount, Date). It links to the Account table so we know exactly which account made the move. One account can have many transaction history rows.

> 🛡️ **Data Cleanup:** We use a rule called `ON DELETE CASCADE`. This means if you delete a customer's profile, the system automatically deletes their bank accounts and transaction history, keeping the database neat and clean.

---

## 🚀 How to Run the Program

Follow these easy steps to launch the app on your computer using **Apache NetBeans** and your local **MySQL** server:

### Prerequisites
1. Have **Java** and **Apache NetBeans** installed.
2. Have your local **MySQL Server** instance active and running.

### Step 1: Create the Database
1. Open your database management program (like **MySQL Workbench**).
2. Open a new query tab, paste your SQL table creation script inside, and hit the **Lightning Bolt (Execute)** icon.
3. Refresh your sidebar to make sure the database `banking_db` pops up.

### Step 2: Open the Project in NetBeans
1. Open **Apache NetBeans**.
2. Go to the top left menu: **File > Open Project...**
3. Select your project folder (`BankingSystemCRUD_LastName_FirstName`) and click **Open**.

### Step 3: Put in Your Database Password
1. In the NetBeans project navigator on the left, expand your source files.
2. Go into the `config` package and open **`DatabaseConnection.java`**.
3. Look for the line that says `private static final String PASSWORD = "...";` and change the text inside the quotation marks to match your personal MySQL database password.

### Step 4: Add the MySQL Connector Driver
1. In the NetBeans left sidebar, right-click the **Libraries** folder inside your project tree.
2. Click **Add Library...**
3. Scroll down the popup menu, select **MySQL JDBC Driver**, and click **Add Library**. (This acts as the bridge connecting your Java windows to your SQL tables).

### Step 5: Click Run!
1. Expand the `ui` package folder inside NetBeans.
2. Right-click on **`MainDashboard.java`** and click **Run File** (or press **Shift + F6**).
3. The main control panel will open up on your screen. You can now freely click around to manage accounts and make transactions!
