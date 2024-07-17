# Pure domain classes
A pure domain class focuses exclusively on the business logic and rules of the application, without any concerns about infrastructure or external systems. 
By maintaining this separation, the codebase becomes more modular, testable, and easier to maintain.

# Characteristics of pure domain classes

What are some of the characteristics of pure domain classes?

1. Encapsulation of Business Logic:

The class should encapsulate the core business rules and logic.
Example: In a banking application, a User class might contain methods for depositing and withdrawing money, including the necessary validations.

2. Independence from Infrastructure:

The class should not depend on or interact with infrastructure-related concerns such as databases, file systems, networks, or user interfaces.
Example: A domain class should not have methods for saving itself to a database.

3. Focus on the Domain Model:

The class should represent concepts, entities, or value objects within the business domain.
Example: Classes like User, Transaction, Account, Balance, and Username are examples of domain entities and value objects.
Persistence Ignorance:

4. The class should not contain any code related to the persistence of its state. Persistence should be handled by repositories or services.
Example: The User class should not have methods like save() or load().
No Dependency on Frameworks:

5. The class should not depend on external libraries or frameworks, except for basic utilities like collections or basic types.
Example: The User class should not import and use Spring annotations or JPA entities directly.

# Refactoring to use Hexagonal Architecture

Our domain classes are pure, but we need to organize our code in a way that is in line with hexagonal architecture.  Let's repackage our application to be in line with hexagonal architecture.

We want a separate package for our domain classes - that represents the "inside" of our hexagon, which of course is an imaginary boundary.

Adapters sit outside the domain package and outside the hexagon in their own adapter package.

So, YOUR GOALS in this milestone are  2 things:

1. Create a new `ConsoleAdapter` class that separates the UI logic from the core application logic to align with Hexagonal principles.

Follow these steps to create that class:

```
Extract the console interaction logic from BankingApplication.
Define methods to display menu and handle user choices.
Delegate actions to the BankingService.
Update the BankingApplication Class

Instantiate the BankingService and ConsoleAdapter.
Call consoleAdapter.run() to start the application.
```

2. Re-package the application to look like this and to be more in line with Hexagonal architecture:

```
src/main/java/com/example
├── application
│   ├── service
│   │   └── BankingService.java
├── domain
│   ├── model
│   │   ├── Balance.java
│   │   ├── Transaction.java
│   │   ├── User.java
│   │   └── Username.java
├── infrastructure
│   ├── adapter
│   │   └── ConsoleAdapter.java
└── BankingApplication.java

```








