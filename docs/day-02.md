# Day 2 – Database Connection & Testing

## Goal

Understand how the Spring Boot banking application connects to PostgreSQL
and learn the basics of testing in a Spring Boot project.

---

## 1. PostgreSQL

PostgreSQL is the relational database used by this project.

The application uses:

- Database: bankapp
- Username: postgres
- Port: 5432

PostgreSQL stores application data such as:

- Users
- Accounts
- Transactions
- Notifications

---

## 2. Spring Boot

Spring Boot is the Java framework used to build the backend application.

This project uses:

- Java 17
- Spring Boot 3.1.2
- Maven

Spring Boot helps us build:

- REST APIs
- Database connections
- Security
- Testing

---

## 3. REST API

A REST API allows applications to communicate with the backend.

Common HTTP methods:

- GET – retrieve data
- POST – create/send data
- PUT – update data
- DELETE – delete data

Example:

```text
POST /api/auth/login