# Bank-Customer-Database-Management

This project is a complete SQLite3-based banking database system.
It includes designing a database schema, creating customer and account-related tables, inserting sample banking data, and executing SQL queries to analyze banking insights.

The goal of this project is to demonstrate SQL concepts such as **table design, relationships, joins, grouping, aggregations, subqueries, and data analysis** using a realistic banking model.

---

# **Project Overview**

This SQLite3 project simulates a simplified banking system.
It includes:

* A fully structured relational database
* Tables for customers, accounts, and transactions
* SQL scripts that insert sample banking data
* Query exercises and solutions
* Use of joins, aggregations, sorting, filtering, and subqueries

This project is ideal for beginners to understand **real-world relational database design**.

---

**Database Design**

The database contains the following main entities:

* BANK_CUSTOMER (customer_id,customer_name,Address,state_code,Telephone)

* BANK_CUSTOMER_EXPORT(customer_id,customer_name,Address,state_code,Telephone)

* Bank_Account_Details(Customer_id,Account_Number,Account_type,Balance_amount,Account_status,Relationship_type) 

* BANK_ACCOUNT (Customer_id,Account_Number,Account_type,Balance_amount,Account_status, Relation_ship)

* Bank_Account_Relationship_Details(Customer_id,Account_Number,Account_type,Linking_Account_Number)
 
* BANK_ACCOUNT_TRANSACTION(Account_Number,Transaction_amount,Transcation_channel,Province,Transaction_Date)
 
* BANK_CUSTOMER_MESSAGES(Event,Customer_message,Notice_delivery_mode) 

* BANK_INTEREST_RATE(account_type,interest_rate,month,year)






**ERD for Your Banking Database**

```
                                   +-----------------------------+
                                   |        BANK_CUSTOMER        |
                                   +-----------------------------+
                                   | customer_id (PK)            |
                                   | customer_name               |
                                   | Address                     |
                                   | state_code                  |
                                   | Telephone                   |
                                   +-----------------------------+
                                            | 1
                                            |
                                            | M
        +---------------------------------------------------------------+
        |                                                               |
+-------------------------------+                 +-------------------------------+
|     BANK_CUSTOMER_EXPORT      |                 |   BANK_CUSTOMER_MESSAGES      |
+-------------------------------+                 +-------------------------------+
| customer_id (FK)              |                 | Event (PK or Unique)          |
| customer_name                 |                 | Customer_message               |
| Address                       |                 | Notice_delivery_mode           |
| state_code                    |                 +-------------------------------+
| Telephone                     |
+-------------------------------+


                       +--------------------------------------+
                       |            BANK_ACCOUNT               |
                       +--------------------------------------+
                       | Customer_id (FK)                     |
                       | Account_Number (PK)                  |
                       | Account_type                         |
                       | Balance_amount                       |
                       | Account_status                       |
                       | Relation_ship                        |
                       +--------------------------------------+
                                  | 1
                                  |
                                  | M
               +----------------------------------------------+
               |             Bank_Account_Details             |
               +----------------------------------------------+
               | Customer_id (FK)                             |
               | Account_Number (FK)                          |
               | Account_type                                 |
               | Balance_amount                               |
               | Account_status                               |
               | Relationship_type                            |
               +----------------------------------------------+


                       +----------------------------------------------+
                       |     Bank_Account_Relationship_Details        |
                       +----------------------------------------------+
                       | Customer_id (FK)                             |
                       | Account_Number (FK)                          |
                       | Account_type                                 |
                       | Linking_Account_Number                       |
                       +----------------------------------------------+


                                  +--------------------------------------+
                                  |      BANK_ACCOUNT_TRANSACTION         |
                                  +--------------------------------------+
                                  | Account_Number (FK)                  |
                                  | Transaction_amount                   |
                                  | Transaction_channel                  |
                                  | Province                             |
                                  | Transaction_Date                     |
                                  +--------------------------------------+

+--------------------------------------------------------------+
|                     BANK_INTEREST_RATE                       |
+--------------------------------------------------------------+
| account_type                                                |
| interest_rate                                               |
| month                                                       |
| year                                                        |
+--------------------------------------------------------------+
```

---

**Relationship Explanation**

* **BANK_CUSTOMER → BANK_ACCOUNT** : One customer can have multiple accounts **(1-to-many)**

* **BANK_CUSTOMER → BANK_CUSTOMER_EXPORT** : Export table stores snapshots of customer data **(1-to-many)**

* **BANK_CUSTOMER → BANK_CUSTOMER_MESSAGES**  :  Customers receive multiple notices/messages **(1-to-many)**

* **BANK_ACCOUNT → Bank_Account_Details** : Additional details stored for each account  **(1-to-1 or 1-to-many)** depending on logic

* **BANK_ACCOUNT → BANK_ACCOUNT_TRANSACTION**   :  Each account can have many transactions **(1-to-many)**

* **BANK_ACCOUNT → Bank_Account_Relationship_Details**  :  Used for linked accounts / joint accounts   **(1-to-many)**

* **BANK_INTEREST_RATE** : Independent lookup table for interest rate by account type

---

# Queries Included

Some examples of queries solved in this project:

**Customer-related Queries**

* List all customers
* Count total customers

**Account-related Queries**

* Show all account balances
* Total balance per customer
* Accounts sorted by highest balance
  
**Transaction-related Queries**

* Transaction history on specific date
* Total deposits/withdrawals
* Transactions grouped by type

**Join Queries**

* Customer details + account details
* Customer → account → transaction mapping
* Account_type Relations
---

**Technologies Used**

* **SQLite3** (Python sqlite3 module / DB Browser for SQLite)
* SQL (DDL + DML)
* Google colab

---

