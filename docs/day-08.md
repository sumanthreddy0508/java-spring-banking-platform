# Day 8 – Validation, Exception Handling & DTOs

## Goal

Understand how Spring Boot validates incoming data, handles errors, and uses DTOs to transfer data between the client and application.

## What I Learned

### 1. Validation

Validation checks whether incoming data is acceptable before the application processes it.

Examples:

- Required fields
- Positive amounts
- Valid email addresses
- Valid input formats

Common validation annotations:

- `@NotNull`
- `@NotBlank`
- `@NotEmpty`
- `@Size`
- `@Min`
- `@Max`
- `@Positive`
- `@Email`

### 2. @Valid

`@Valid` tells Spring to validate an incoming request object according to its validation rules.

Example:

`@Valid @RequestBody`

`@RequestBody` converts incoming JSON into a Java object, while `@Valid` checks the validation rules on that object.

### 3. Exception Handling

An exception occurs when something goes wrong while the application is running.

Example from the banking application:

`AccountService.getAccount(id)` can result in an exception when an account cannot be found.

The application uses `try/catch` blocks to handle some runtime errors and return an appropriate response.

### 4. HTTP Status Codes

Important HTTP status codes learned:

- `200` – Success
- `201` – Created
- `400` – Bad Request
- `401` – Unauthorized
- `403` – Forbidden
- `404` – Not Found
- `500` – Internal Server Error

The AccountController uses `403` when the authenticated user does not have permission to access an account and `404` when an account cannot be found.

### 5. DTO

DTO stands for Data Transfer Object.

A DTO is used to transfer data between different parts of an application or between the client and application.

DTOs can help separate the API model from the database entity and control which fields are exposed.

### 6. NotificationRequest

The project contains `NotificationRequest.java`.

It contains:

- `recipient`
- `subject`
- `content`

These fields use `@NotBlank` validation.

Examples:

`@NotBlank(message = "Recipient is required")`

`@NotBlank(message = "Subject is required")`

`@NotBlank(message = "Content is required")`

This means these fields cannot be blank.

### 7. NotificationDto

The project also contains `NotificationDto.java`.

It contains:

- `id`
- `recipient`
- `subject`
- `content`
- `notificationType`
- `sentAt`
- `status`
- `read`

The class uses Lombok annotations:

- `@Data`
- `@NoArgsConstructor`
- `@AllArgsConstructor`

### DTO vs Request DTO

A simple way to understand the difference:

Request DTO:
- Used for incoming request data.
- Can contain validation rules.
- Example: `NotificationRequest`

DTO:
- Used to transfer application data.
- Can contain information needed by another layer or returned to a client.
- Example: `NotificationDto`

## Application Flow

Client
→ Request DTO
→ Validation
→ Controller
→ Service
→ Data Access
→ Database
→ DTO
→ Response

## Interview Questions

### What is validation?

Validation checks whether incoming data meets the application's requirements before processing it.

### What is exception handling?

Exception handling is the process of handling errors that occur while an application is running so that the application can return an appropriate response instead of failing unexpectedly.

### What is a DTO?

DTO stands for Data Transfer Object. It is used to transfer data between application layers or between the client and application while controlling the data being transferred.

### What is the difference between @RequestBody and @Valid?

`@RequestBody` converts incoming JSON into a Java object.

`@Valid` tells Spring to validate that object using its validation rules.

### Why use DTOs?

DTOs help separate the API/data-transfer model from the database entity and allow the application to control what data is received or exposed.

## Day 8 Status

Completed learning about Spring Boot validation, exception handling, HTTP status codes, DTOs, and validation in the existing banking application.

Reviewed `NotificationRequest` and `NotificationDto` from the project.

No application code was changed today.