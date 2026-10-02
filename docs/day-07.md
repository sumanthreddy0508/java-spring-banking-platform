# Day 7 – Spring Boot Controller and Service Architecture

## Goal

Understand how an API request moves through the Spring Boot application.

## What I Learned

### Controller

A Controller receives HTTP/API requests from the client.

The AccountController uses:

- `@RestController`
- `@RequestMapping`
- `@GetMapping`
- `@PostMapping`
- `@PutMapping`
- `@PathVariable`
- `@RequestBody`

The controller is mapped to:

`/api/accounts`

### REST API Methods

- GET – retrieve data
- POST – create or perform an operation
- PUT – update data
- DELETE – remove data

### Service Interface

`AccountService` is an interface that defines the operations available for account management.

Examples:

- `createAccount()`
- `getAccount()`
- `deposit()`
- `withdraw()`
- `updateAllBalancesTo5000()`

An interface defines WHAT operations are available.

### Service Implementation

`AccountManager` implements `AccountService`.

The `@Service` annotation tells Spring to manage it as a service component.

The implementation contains the actual business logic.

### Repository

The service implementation uses `AccountRepository` to work with account data.

### Application Flow

Client / Postman
→ Controller
→ Service Interface
→ AccountManager
→ Repository
→ PostgreSQL

## Key Takeaway

Controller = receives the request

Service Interface = defines the operations

Service Implementation = contains the business logic

Repository = works with the database

Entity = represents application data

## Day 7 Status

Completed a practical review of the Controller → Service Interface → Service Implementation → Repository architecture using the existing banking application.

No application code was changed today.