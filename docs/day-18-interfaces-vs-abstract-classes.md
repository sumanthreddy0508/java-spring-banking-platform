\# Day 18 — Interfaces vs Abstract Classes



\## Date

October 23, 2026



\## Topic

Interfaces vs Abstract Classes in Java



\---



\# 1. Day 18 Goal



Today I learned the difference between:



\- Interfaces

\- Abstract classes

\- Abstract methods

\- Concrete methods

\- `implements`

\- `extends`

\- Interface abstraction

\- Class inheritance

\- How abstraction is used in my banking project



The main project relationship studied today was:



```text

AccountController

&#x20;      ↓

AccountService

&#x20;      ↓

AccountManager

&#x20;      ↓

AccountRepository

&#x20;      ↓

PostgreSQL

```



The main focus was the relationship between:



```text

AccountService

&#x20;      ↓

AccountManager

```



\---



\# 2. What is an Interface?



An interface is a contract that defines operations that a class must provide.



Example from the banking project:



```java

public interface AccountService {



&#x20;   Optional<Account> getAccount(int id);



&#x20;   Account deposit(int id, double amount);



&#x20;   Account withdraw(int id, double amount);

}

```



The interface defines WHAT operations are available.



It does not contain the main business implementation used by `AccountManager`.



In simple terms:



```text

AccountService = WHAT the service can do

AccountManager = HOW the service does it

```



\---



\# 3. AccountService in My Banking Project



My project uses `AccountService` as an interface.



The interface defines operations such as:



```text

getAccount()

deposit()

withdraw()

createAccount()

updateAllBalancesTo5000()

```



The purpose is to define a clear service contract.



The controller can depend on the service interface instead of being directly tied to the implementation.



Conceptually:



```text

AccountController

&#x20;      ↓

AccountService

&#x20;      ↓

AccountManager

```



\---



\# 4. What is AccountManager?



`AccountManager` is the implementation of `AccountService`.



It contains the actual business logic.



The class uses:



```java

implements AccountService

```



This means `AccountManager` agrees to provide the operations defined by `AccountService`.



Example:



```java

public class AccountManager implements AccountService {

&#x20;   // actual business logic

}

```



The important idea is:



```text

AccountService

&#x20;   ↓

Defines the contract



AccountManager

&#x20;   ↓

Implements the contract

&#x20;   ↓

Contains business logic

```



\---



\# 5. Business Logic in AccountManager



The banking project's `AccountManager` contains business rules.



For example, during a withdrawal:



```text

Check that amount is positive

&#x20;       ↓

Check that account exists

&#x20;       ↓

Check available balance

&#x20;       ↓

Check insufficient funds

&#x20;       ↓

Subtract amount

&#x20;       ↓

Save updated account

```



A business rule from the project is:



```java

if (account.getBalance() < amount) {

&#x20;   throw new IllegalArgumentException("Insufficient funds");

}

```



This is business logic and belongs in the service/business layer rather than the controller.



\---



\# 6. What is an Abstract Class?



An abstract class is a class that is designed to be inherited by another class.



General Java example:



```java

abstract class Account {



&#x20;   String accountNumber;



&#x20;   abstract void calculateInterest();



&#x20;   void displayAccount() {

&#x20;       System.out.println("Account: " + accountNumber);

&#x20;   }

}

```



An abstract class can contain:



\- Variables

\- Abstract methods

\- Concrete methods

\- Constructors

\- Other normal class members



An abstract class can therefore provide both a structure and some shared implementation.



\---



\# 7. Abstract Method



An abstract method is a method declared without an implementation.



Example:



```java

abstract void calculateInterest();

```



The method has no body.



A child class must provide the implementation.



Example:



```java

class SavingsAccount extends Account {



&#x20;   @Override

&#x20;   void calculateInterest() {

&#x20;       System.out.println("Calculating savings interest");

&#x20;   }

}

```



The important rule is:



```text

Abstract method

&#x20;       ↓

Child class must implement it

```



\---



\# 8. Concrete Method



A concrete method already contains an implementation.



Example:



```java

void displayAccount() {

&#x20;   System.out.println("Account: " + accountNumber);

}

```



A child class can inherit and use this method.



It does not have to implement it.



Therefore:



```text

Abstract method

→ Must be implemented by the child



Concrete method

→ Already has implementation

→ Can be inherited or overridden

```



\---



\# 9. Interface vs Abstract Class



\## Interface



An interface is primarily used to define a contract.



Example:



```java

public interface AccountService {



&#x20;   Account deposit(int id, double amount);



&#x20;   Account withdraw(int id, double amount);

}

```



A class implements the interface:



```java

public class AccountManager implements AccountService {

}

```



\## Abstract Class



An abstract class is a partially implemented class.



Example:



```java

abstract class Account {



&#x20;   abstract void calculateInterest();



&#x20;   void displayAccount() {

&#x20;       System.out.println("Account");

&#x20;   }

}

```



A child class inherits from the abstract class:



```java

class SavingsAccount extends Account {

&#x20;   

&#x20;   @Override

&#x20;   void calculateInterest() {

&#x20;       // implementation

&#x20;   }

}

```



\---



\# 10. implements vs extends



This is an important Java rule.



\## implements



Used when a class implements an interface.



Example from my project:



```java

public class AccountManager implements AccountService {

}

```



Remember:



```text

Interface

&#x20;   ↓

implements

&#x20;   ↓

Class

```



\## extends



Used when one class inherits from another class.



General example:



```java

class SavingsAccount extends Account {

}

```



Remember:



```text

Parent class

&#x20;   ↓

extends

&#x20;   ↓

Child class

```



\---



\# 11. Simple Comparison



```text

INTERFACE



AccountService

&#x20;     ↓

&#x20; implements

&#x20;     ↓

AccountManager

```



```text

ABSTRACT CLASS



Account

&#x20;     ↓

&#x20;  extends

&#x20;     ↓

SavingsAccount

```



\---



\# 12. Why My Project Uses AccountService



The banking project uses:



```text

AccountController

&#x20;      ↓

AccountService

&#x20;      ↓

AccountManager

```



Instead of making the controller directly responsible for all business logic, the responsibilities are separated.



The controller handles requests.



The service defines the operations.



The service implementation handles business logic.



The repository communicates with the database.



This gives a cleaner architecture.



\---



\# 13. Loose Coupling



Using an interface helps reduce tight coupling.



Instead of thinking:



```text

Controller → AccountManager directly

```



the project uses:



```text

Controller → AccountService → AccountManager

```



The controller depends on the service contract.



This makes the application easier to maintain, test, and change.



\---



\# 14. Abstraction in My Banking Project



The abstraction flow is:



```text

Postman

&#x20;  ↓

AccountController

&#x20;  ↓

AccountService

&#x20;  ↓

AccountManager

&#x20;  ↓

AccountRepository

&#x20;  ↓

PostgreSQL

```



For example, when a withdrawal request comes into the application:



```text

POST withdrawal request

&#x20;       ↓

AccountController

&#x20;       ↓

AccountService

&#x20;       ↓

AccountManager.withdraw()

&#x20;       ↓

Business validation

&#x20;       ↓

AccountRepository

&#x20;       ↓

PostgreSQL

```



The controller does not need to know every detail of how the withdrawal is processed.



It works with the service contract.



That is one of the benefits of abstraction.



\---



\# 15. Important Project Accuracy



My current banking project definitely uses:



```text

AccountService = interface

AccountManager = implementation

```



I have not confirmed that the current project contains an abstract `Account` class.



Therefore, the abstract `Account` examples in these notes are general Java learning examples, not a claim about the current project implementation.



\---



\# 16. Interface vs Abstract Class — Quick Table



| Feature | Interface | Abstract Class |

|---|---|---|

| Main purpose | Define a contract | Provide abstraction + shared implementation |

| Keyword used by class | `implements` | `extends` |

| Can define methods | Yes | Yes |

| Can have abstract methods | Yes | Yes |

| Can have concrete methods | Yes | Yes |

| Can contain instance state | Interfaces have limitations; classes can have normal instance state | Yes |

| Class relationship | A class implements it | A class extends it |

| Example in my project | `AccountService` | No confirmed abstract class |



\---



\# 17. Interview Question: Why Use an Interface?



A good answer:



> I use an interface to define a clear contract between components and reduce coupling. In my banking project, `AccountService` defines the available account operations, while `AccountManager` implements the interface and contains the business logic. This separation improves maintainability, testing, and flexibility.



\---



\# 18. Interview Question: What is the Difference Between an Interface and Abstract Class?



Answer:



> An interface is primarily used to define a contract that implementing classes must follow, while an abstract class can provide both abstract methods and shared concrete implementation. A class uses `implements` for an interface and `extends` for an abstract class.



\---



\# 19. Interview Question: What is an Abstract Method?



Answer:



> An abstract method is a method declared without an implementation. A concrete child class must provide the implementation for that method.



Example:



```java

abstract void calculateInterest();

```



\---



\# 20. Interview Question: What is a Concrete Method?



Answer:



> A concrete method already has an implementation. A child class can inherit the method or override it if different behavior is required.



\---



\# 21. Interview Question: What is implements?



Answer:



> `implements` is used when a class implements an interface. For example, `AccountManager implements AccountService` means AccountManager provides the implementation required by the AccountService contract.



\---



\# 22. Interview Question: What is extends?



Answer:



> `extends` is used for class inheritance. A child class can inherit fields and methods from a parent class.



Example:



```java

class SavingsAccount extends Account {

}

```



\---



\# 23. Key Concepts Learned Today



```text

Interface

Abstract class

Abstract method

Concrete method

implements

extends

Abstraction

Loose coupling

Service contract

Business logic

AccountService

AccountManager

```



\---



\# 24. Most Important Memory Rules



```text

Interface = Contract



AccountService = WHAT



AccountManager = HOW



implements = Interface



extends = Class inheritance



Abstract method = No implementation



Concrete method = Has implementation



Business logic = AccountManager



Database access = AccountRepository

```



\---



\# 25. Day 18 Final Architecture



```text

&#x20;                BANKING APPLICATION



&#x20;                      Postman

&#x20;                         ↓

&#x20;                 AccountController

&#x20;                         ↓

&#x20;                  AccountService

&#x20;                   (Interface)

&#x20;                         ↓

&#x20;                  AccountManager

&#x20;                 (Implementation)

&#x20;                         ↓

&#x20;                 AccountRepository

&#x20;                         ↓

&#x20;                    PostgreSQL

```



This architecture demonstrates abstraction, separation of responsibilities, loose coupling, and the use of interfaces in a Spring Boot application.



\---



\# 26. Day 18 Summary



Today I learned the difference between interfaces and abstract classes.



I learned that an interface defines a contract, while an abstract class can provide both abstract methods and shared implementation.



In my banking project, `AccountService` is an interface and `AccountManager` implements it.



`AccountService` defines WHAT operations are available, while `AccountManager` contains HOW those operations are performed.



I also learned the difference between `implements` and `extends`, abstract methods and concrete methods, and how abstraction helps create a cleaner and more maintainable Spring Boot architecture.



\## Status



Day 18 — Completed

Topic: Interfaces vs Abstract Classes

Project connection: AccountService → AccountManager

GitHub documentation: `docs/day-18-interfaces-vs-abstract-classes.md`

