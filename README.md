# check-user-account-status
A Simple Mule Project that checks the user's account inactive status and sends message to a ActiveMQ queue.

# MuleSoft XA Transaction POC

## 🚀 Project Overview
This project demonstrates a MuleSoft implementation of XA-Transaction combining Oracle Database operations and ActiveMQ messaging. The application:

* Updates inactive user accounts and sends JMS message.  
* Deletes user accounts based on inactivity and sends JMS message.  
* Ensures DB and JMS operations participate in a single XA Transaction.  

---

## ⚙️ Technologies Used
- **MuleSoft**
- **Oracle Database XE**
- **ActiveMQ (JMS Broker)**
- **Bitronix Transaction Manager**
- **Postman**

---

## 🏗️ Database Setup Instructions

### 1️⃣ Oracle Database Setup
1. Start Oracle Database (XE recommended).
2. Connect to the database as system user or to the available user
   
```sql
-- As SYSTEM or SYSDBA:

CREATE TABLE user_accounts (
    USERNAME VARCHAR2(50) PRIMARY KEY,
    EMAIL_ADDRESS VARCHAR2(100),
    ACCOUNT_CREATED_ON DATE,
    LAST_LOGGED_IN DATE,
    ACCOUNT_STATUS VARCHAR2(20),
    STATUS_UPDATED_ON DATE,
    ALERT_SENT VARCHAR2(5)
);

-- Insert Dummy Data:

INSERT INTO user_accounts (
    username,
    email_address,
    account_created_on,
    last_logged_in,
    account_status,
    status_updated_on,
    alert_sent
) VALUES (
    'user15',
    'user15@test.com',
    '01-JAN-24',
    '01-JUL-24',
    'ACTIVE',
    '01-JUL-24',
    'NO'
);

COMMIT;
```

## Key Features
- XA Transaction to ensure DB and JMS operations succeed or rollback together.
