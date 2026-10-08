# Day 10 – REST APIs and Postman

## What I Learned

Today I learned how REST APIs work in the Spring Boot banking application.

## REST API Request Flow

Postman
→ AccountController
→ AccountService
→ AccountManager
→ AccountRepository
→ PostgreSQL

## GET Request

GET is used to retrieve data.

Example:

GET /api/accounts/1

This requests the account with ID 1.

The `{id}` is a path variable.

Example:

/api/accounts/{id}

/api/accounts/1

Here, the account ID is 1.

## Account Controller

The request reaches `AccountController`.

The controller passes the account ID to:

```java
accountService.getAccount(id)