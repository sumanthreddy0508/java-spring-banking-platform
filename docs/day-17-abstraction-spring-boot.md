\# Day 17 – Abstraction \& Spring Boot Architecture



\## Date

October 21, 2026



\## Objective



Today I learned abstraction, interfaces, business logic, dependency injection, loose coupling, and the Controller → Service → Repository flow using my actual Spring Boot banking application.



The main goal was to understand these concepts through my own project instead of learning only generic Java examples.



\---



\# 1. Abstraction



Abstraction means hiding unnecessary implementation details and exposing only what is required.



In my banking application, when a user sends:



GET /api/accounts/1



the user does not need to know:



\- How Java finds the account

\- How AccountManager processes the request

\- How AccountRepository accesses the database

\- How JPA/Hibernate works internally

\- How PostgreSQL stores the data



The user only needs the account information.



\### My project flow



Postman

&#x20;   ↓

AccountController

&#x20;   ↓

AccountService

&#x20;   ↓

AccountManager

&#x20;   ↓

AccountRepository

&#x20;   ↓

PostgreSQL



This separation helps hide internal implementation details from the caller.



\---



\# 2. Interface



An interface defines a contract.



My project contains:



```java

public interface AccountService {



&#x20;   Optional<Account> getAccount(int id);



&#x20;   Account deposit(int id, double amount);



&#x20;   Account withdraw(int id, double amount);



}

