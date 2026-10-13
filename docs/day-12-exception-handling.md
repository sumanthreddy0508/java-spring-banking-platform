\# Day 12 – Java \& Spring Boot Exception Handling



\## 1. Overview



Today I learned how Java and Spring Boot handle exceptions and how application errors can be converted into meaningful HTTP responses.



This topic is important for:



\- Java Developer

\- Junior Java Developer

\- Application Support

\- Technical Support

\- IT Support

\- QA / Software Testing

\- Cloud Support



The main concepts covered today:



\- Exceptions

\- `throw`

\- `try/catch`

\- `RuntimeException`

\- `IllegalArgumentException`

\- `@ExceptionHandler`

\- `@ControllerAdvice`

\- HTTP error responses

\- Business-rule validation

\- Application Support troubleshooting

\- 401 vs 403 vs 404



\---



\# 2. What Is an Exception?



An exception is an event that interrupts the normal flow of program execution because an error or unexpected condition has occurred.



For example, a banking application should not allow a user to withdraw more money than their account balance.



Example:



```java

if (account.getBalance() < amount) {

&#x20;   throw new IllegalArgumentException("Insufficient funds");

}

