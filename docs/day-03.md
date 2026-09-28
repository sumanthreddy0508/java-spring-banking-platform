# Day 3 – Spring Boot Architecture Fundamentals

## Goal

Understand the basic architecture of a Spring Boot backend application
and how the different layers work together.

---

## What I Learned

### 1. Java

Java is the programming language used to build the backend application.

---

### 2. Spring Boot

Spring Boot is a framework used to build Java backend applications
and REST APIs.

It also helps with:

- Database connections
- Security
- Dependency Injection
- Testing
- Application configuration

---

### 3. REST API

A REST API allows different applications to communicate with each other
using HTTP.

Common HTTP methods:

- GET – retrieve data
- POST – create/send data
- PUT – update data
- DELETE – delete data

---

### 4. Controller

A Controller receives HTTP requests and sends them to the appropriate
part of the application.

Examples from this project:

- AuthController
- AccountController
- TransactionController
- NotificationController

---

### 5. Service

The Service layer contains the business logic of the application.

The Controller receives the request and the Service performs the
required business operation.

---

### 6. Repository

The Repository layer is responsible for communicating with the database.

---

### 7. Entity

An Entity represents data that is stored in the database.

Examples:

- Auth
- Account
- Transaction
- Notification

---

### 8. JPA

JPA stands for Java Persistence API.

It provides a standard way for Java applications to work with
relational databases.

---

### 9. Hibernate

Hibernate is an implementation of JPA.

It helps map Java objects to database tables.

---

### 10. PostgreSQL

PostgreSQL is the relational database used by this project.

It stores application data such as users, accounts, transactions,
and notifications.

---

### 11. Dependency Injection

Dependency Injection is a Spring concept where Spring provides the
objects that a class needs.

This reduces the need to create and manage objects manually.

---

### 12. Maven

Maven is used to build the Java project and manage its dependencies.

The project contains:

- pom.xml
- mvnw.cmd

---

## Application Architecture

```text
Client / Postman
       ↓
   Controller
       ↓
     Service
       ↓
   Repository
       ↓
 JPA / Hibernate
       ↓
 PostgreSQL