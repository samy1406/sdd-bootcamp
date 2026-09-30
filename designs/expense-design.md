# Expense Feature Design

## 1. Feature

REQ-TRX-001 — Add Expense

## 2. User Flow
- user will click on the '+' sign to add the expense
- User need to add 
    * Date 
    * Amount
    * Category
    * Account type
    * Note 

- once everything is mentioned it can click on submit to add the expense compulsory.
- validate if entry is correct or not.
- if validation fails show error, if pass save expense, update account, and put as success.
- if save fails, preserve the entry and retry

## 3. Data

### 3.1 Expense Fields
* Date - the user will add the date at which the expense happened
* Amount - the expense amount 
* Category - what type of expense it was 
* Account type - Choose from the account available, such as current account, saving account, credit card, cash
* Note - the user can add the note to remember why they have done this spending.


### 3.2 Data Types
* Date  - use DATE datatype to store the date of expense.
* Amount - use DECIMAL(18,2) data type
* Category - text
* Account type - Drop down from list of available account
* Note - text

### 3.3 Required vs Optional
* Date - Required 
* Amount - Required
* Category - Required
* Account type - Required
* Note - Optional


## 4. Validation
- validate if account belong to authenticated user, yes continue else reject.
- Amount must be a positive numeric value greater than zero, with up to two decimal places.
- the date should be rolling 12 months, today allowed, future dates not allowed and dates older than 12 months not allowed.
- check if all required fields are there or not.
- account type should be validated with available account type.



## 5. Authentication & Authorization
- User must be authenticated.

- Expense must be associated with the authenticated user.

- User cannot access another user's expense.

- Authorization must be enforced server-side.

## 6. Account Balance

<!-- How does adding an expense affect the account balance? -->

## 7. Error Handling

<!-- What should happen when something goes wrong? -->

## 8. API / Application Interface

<!-- How does the frontend/application communicate with
the backend/business logic? -->

## 9. Data Persistence

<!-- Where and how is the expense stored? -->

## 10. Testing Strategy

<!-- What types of tests will verify this feature? -->

## 11. Security Considerations

<!-- What attacks or misuse cases should be considered? -->

## 12. Open Design Questions

<!-- Decisions we still need to make -->