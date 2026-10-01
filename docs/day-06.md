# Day 6 – Understanding Spring Boot Application Architecture

## Goal

Understand how the existing banking application is structured and how requests move through the application.

## What I Learned

### Entity

An Entity is a Java class that represents application data that can be stored in a database.

The project contains entities such as:

- Account
- Auth
- Notification
- Transaction

### Controller

The Controller receives HTTP/API requests from clients such as Postman.

### Service / Business Logic

The business layer contains the logic used to process application operations.

### Data Access / Repository

The data-access layer is responsible for interacting with the database.

### JPA / Hibernate

JPA and Hibernate provide the connection between Java objects and relational database data.

### Application Flow

Client / Postman
→ Controller
→ Service / Business Logic
→ Data Access / Repository
→ JPA / Hibernate
→ PostgreSQL

## Key Takeaways

- Entity represents data.
- Controller handles API requests.
- Service handles business logic.
- Data Access/Repository handles database operations.
- JPA/Hibernate connects Java objects with database records.

## Day 6 Status

Completed a review of the existing Spring Boot project architecture and learned how Controller, Business Logic, Data Access, Entity, JPA/Hibernate, and PostgreSQL work together.

No application code was changed today.