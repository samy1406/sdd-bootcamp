# Product Specification

## 1. Product Overview

### 1.1 Product Name

Personal Expense Tracker

### 1.2 Purpose

The product allows a user to manage and monitor personal financial transactions, including expenses, income, and transfers.

### 1.3 Target User

An individual user who wants to track personal income, expenses, account balances, and spending statistics.

---

## 2. Product Scope

### 2.1 In Scope

The initial product must support:

* User authentication using email and password.
* Adding expenses.
* Adding income.
* Adding transfers.
* Viewing expense summaries.
* Viewing income and expense statistics.
* Viewing account information.
* Managing basic user profile information.

### 2.2 Out of Scope

The following are not currently defined for the initial version:

* Multiple currencies.
* External bank integration.
* Notifications.
* Automated transaction import.
* Mobile application.

These items may be reconsidered in a future version.

---

## 3. User Roles

### 3.1 User

A registered and authenticated user who can manage their own financial information.

---

## 4. Authentication

### REQ-AUTH-001 — User Login

The system must provide a login page that allows a user to authenticate using an email address and password.

### REQ-AUTH-002 — Authentication Protection

Application functionality that requires an authenticated user must not be accessible without successful authentication.

### REQ-AUTH-003 — Password Update

An authenticated user must be able to update their password through an authenticated process.

---

## 5. Transactions

### REQ-TRX-001 — Add Expense

An authenticated user must be able to add an expense.

An expense must contain:

* Date
* Amount
* Category
* Account type
* Note

### REQ-TRX-002 — Add Income

An authenticated user must be able to add an income transaction.

### REQ-TRX-003 — Add Transfer

An authenticated user must be able to add a transfer transaction.

### REQ-TRX-004 — Add Transaction Access

Expense, income, and transfer creation must be accessible from the application's transaction creation interface.

### REQ-TRX-005 — Transaction Ownership

A user must only be able to access and modify their own financial transactions.

### Acceptance Criteria
AC-TRX-001 - Succesfully add an expense
- Given the user is authenticated
- when the user enters a valid date, amount, category, account type and note and submits the expense.
- then the system must create the expense successfully
- And the expense must be associated with the authenticated user.

AC-TRX-002 — Required Expense Information

- Given the user is authenticated
- When the user submits an expense with one or more required fields missing
- Then the system must reject the submission
- And indicate which required information is missing.

AC-TRX-003 — Invalid Amount

- Given the user is authenticated
- When the user enters a non-numeric value as the expense amount
- Then the system must reject the expense
- And display an appropriate validation message.
- non numeric amounts are rejected.

AC-TRX-004 — Unauthorized Expense Creation

- Given the user is not authenticated
- When the user attempts to access or submit the expense creation functionality
- Then the system must deny the request
- And the expense must not be created.

AC-TRX-005 — Expense Ownership

- Given an authenticated user has created an expense
- When another authenticated user attempts to access or modify that expense
- Then the system must deny the request.

AC-TRX-006 — Successful Persistence

- Given the user submits a valid expense
- When the system accepts the expense
- Then the expense must be persisted
- And it must be available when the user views their transactions again.

AC-TRX-007 — Account Balance Update

- Given the user has an account associated with the expense
- When the expense is successfully created
- Then the applicable account balance must be updated according to the transaction rules.
---

## 6. Amount Validation

### REQ-VAL-001 — Numeric Amount

The transaction amount field must accept numeric values.

### REQ-VAL-002 — Invalid Amount Handling

The system must reject values that do not satisfy the defined amount validation rules.

The exact rules for zero, negative values, decimal values, and maximum values are to be defined.

---

## 7. Dashboard

### REQ-DASH-001 — Daily Expense

The front page must display the user's daily expense.

### REQ-DASH-002 — Weekly Expense

The front page must display the user's weekly expense.

### REQ-DASH-003 — Monthly Expense

The front page must display the user's monthly expense.

### REQ-DASH-004 — Yearly Expense

The front page must display the user's yearly expense.

---

## 8. Statistics

### REQ-STAT-001 — Income Statistics

The system must display information about the user's income.

### REQ-STAT-002 — Expense Statistics

The system must display information about the user's expenses.

### REQ-STAT-003 — Category Expense Breakdown

The system must provide an expense breakdown based on the categories assigned to expenses.

### REQ-STAT-004 — Expense Visualization

The expense category breakdown must be represented using a pie chart.

---

## 9. Account Information

### REQ-ACC-001 — Account Information Display

The application must display account-related information to the authenticated user.

### REQ-ACC-002 — Credit and Debit Updates

Income and expense transactions must update the corresponding account information.

### REQ-ACC-003 — Updated Balance

The account information must reflect the latest applicable transaction data.

---

## 10. User Interface

### REQ-UI-001 — Add Transaction Button

The application must provide a "+" button that allows the user to initiate:

* Expense
* Income
* Transfer

### REQ-UI-002 — Transaction Form

The expense form must provide fields for:

* Date
* Amount
* Category
* Account type
* Note

### REQ-UI-003 — User Information

The application must display the user's name.

### REQ-UI-004 — Stats and Account Navigation

The application must provide access to the user's statistics and account information.

---

## 11. Profile

### REQ-PROF-001 — Profile Photo

The user must be able to add a profile photo.

### REQ-PROF-002 — Password Management

The user must be able to update their password through an authenticated process.

---

## 12. Security Requirements

### REQ-SEC-001 — Login Bypass Prevention

An unauthenticated user must not be able to access protected application functionality by bypassing the login interface.

### REQ-SEC-002 — Cross-Account Access Prevention

A user must not be able to access another user's account or financial information.

### REQ-SEC-003 — Protected Transaction Access

Transaction data must be associated with the authenticated user and protected from unauthorized access.

---

## 13. Acceptance Criteria

Acceptance criteria will be defined for each feature specification before implementation.

Each acceptance criterion must describe:

* Preconditions
* User action
* Expected system behaviour
* Relevant failure or edge conditions

---

## 14. Edge Cases

The following areas require explicit edge-case definitions before the relevant features are implemented:

* Invalid email
* Incorrect password
* Empty required fields
* Non-numeric amount
* Zero amount
* Negative amount
* Very large amount
* Unauthorized page access
* Unauthorized transaction access
* Missing account information
* Invalid transaction category
* Profile photo validation
* Password update failure

---

## 15. Non-Functional Requirements

### 15.1 Usability

The application should be simple and easy to understand.

### 15.2 Visual Design

The initial interface should use a simple visual design with minimal decorative graphics.

### 15.3 Maintainability

The implementation should follow the engineering and code-quality rules defined in the project constitution.

---

## 16. Assumptions

* The application is intended for individual personal financial tracking.
* Users must authenticate before accessing protected financial information.
* Transactions belong to the authenticated user.
* Expense categories are available when recording expenses.

---

## 17. Open Questions

The following decisions must be made before their affected features are finalized:

1. What account types are supported?
2. Can a user have multiple accounts?
3. What transaction fields are required for income?
4. What transaction fields are required for transfers?
5. Can users edit transactions after creation?
6. Can users delete transactions?
7. What is the exact rule for zero and negative amounts?
8. Are decimal amounts allowed?
9. How should dates and time zones be handled?
10. How should the account balance be calculated?
11. What happens when a transfer is made between two accounts?
12. What image formats and size limits are allowed for profile photos?
13. What password requirements apply?
14. What does "live" account updating mean for this application?
15. Should the dashboard show only expenses or both income and expenses?

---

## 18. Future Enhancements

Features not yet committed to the initial release can be evaluated after the MVP is validated.
