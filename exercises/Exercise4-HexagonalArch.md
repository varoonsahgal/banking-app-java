# Pure domain classes
A pure domain class focuses exclusively on the business logic and rules of the application, without any concerns about infrastructure or external systems. 
By maintaining this separation, the codebase becomes more modular, testable, and easier to maintain.

# Characteristics of pure domain classes

What are some of the characteristics of pure domain classes?

Encapsulation of Business Logic:

1. The class should encapsulate the core business rules and logic.
Example: In a banking application, a User class might contain methods for depositing and withdrawing money, including the necessary validations.
Independence from Infrastructure:

2. The class should not depend on or interact with infrastructure-related concerns such as databases, file systems, networks, or user interfaces.
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

# Characteristics of pure domain classes




