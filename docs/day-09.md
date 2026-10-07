# Day 9 – Service & Business Logic

## What I Learned

Today I learned how the Service layer handles business logic in a Spring Boot application.

### Project Flow

Controller
→ Service Interface
→ Service Implementation
→ Repository
→ PostgreSQL Database

## AccountService

`AccountService` is an interface.

It defines WHAT operations the application supports:

- createAccount()
- getAccount()
- deposit()
- withdraw()
- updateAllBalancesTo5000()

## AccountManager

`AccountManager` implements `AccountService`.

It contains the actual business logic.

Important annotation:

```java
@Service