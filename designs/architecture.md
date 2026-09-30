# System Architecture

## Technology Stack

### Frontend
HTML + CSS + JavaScript

### Backend
Python + FastAPI

### Database
SQLite

### Testing
pytest

### Development Environment
GitHub Codespaces

## Data Model

### User

- User ID
- Name
- Email
- Password
- Profile photo

### Account
### Account

- Account ID
- Account name
- Account type
- Balance
- User ID

### Expense
- Expense ID
- Date
- Amount
- Category
- Account ID
- Note
- User ID

### Category
- Category ID
- Category name
- User ID

## Relationships

- A User can have multiple Accounts.
- A User can have multiple Categories.
- A User can have multiple Expenses.
- Each Expense belongs to one User.
- Each Expense is associated with one Account.
- Each Expense is associated with one Category.

## Authentication

- The user logs in using email and password.
- The backend verifies the credentials.
- Invalid credentials are rejected.
- A successful login creates an authenticated session.
- Protected application features require an authenticated session.

## Authorization

- Every protected request must identify the authenticated user.
- A user may access only resources that belong to that user.
- A user must not be able to access another user's expenses or accounts.
- Authorization checks must be enforced by the backend.
- The frontend must not be the only security control.

## Expense Creation Flow

1. User logs in and receives an authenticated session.
2. User clicks the "+" button.
3. User selects Expense.
4. User enters Date, Amount, Category, Account, and optional Note.
5. Backend validates the submitted data.
6. Backend verifies that the selected Account belongs to the authenticated user.
7. Backend creates the Expense and associates it with the authenticated user.
8. The corresponding Account balance is updated.
9. The system returns a success response.
10. If saving fails, the entered data must be preserved so the user can retry.

## Account Balance Consistency

- Creating an expense and updating the account balance must be treated as one logical operation.
- If either operation fails, the system must not leave the account and expense data inconsistent.
- A failed operation must not result in an expense being recorded without the corresponding account balance update.

## Error Handling

- Invalid user input must return a clear validation error.
- Unauthorized requests must be rejected.
- If expense creation fails, the user must be informed that the expense was not created.
- Entered expense data should be preserved so the user can retry.
- Unexpected system errors must not expose sensitive information.

## Testing Strategy

- Unit tests will validate individual validation and business rules.
- Integration tests will validate database operations and authenticated requests.
- Security tests will verify that unauthenticated users and other users cannot access protected data.
- Acceptance tests will verify the feature against its defined acceptance criteria.