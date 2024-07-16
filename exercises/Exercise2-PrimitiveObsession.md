# Identifying and Refactoring the Primitive Obsession code smell


### 1. Identify Primitive obsession

Your first goal is to identify primitive obsession in your banking application code. You should look out for the following signs:

- Usage of Primitive Types to Represent Domain Concepts
Example: Using String to represent an email address, phone number, or social security number.
Indicator: Repeated code to validate or manipulate these strings.

- Lack of Domain-Specific Types
Example: Using int, double, or String for concepts that have specific rules or behaviors, like money, coordinates, or dates.
Indicator: You see the same validation or business logic spread across multiple methods.

- It's an unconstrained type - if there's no boundaries on possible values and it's NOT a local variable

Once you identify a candidate for primitive obsession, take note.



### 2. Refactor to fix Primitive Obsession

There are 3 candidates for primitive obsession that you now need to fix:

1. `private String username;` - why?  because using String for usernames can be considered a form of primitive obsession if
   usernames have specific rules or behaviors associated with them (e.g., length restrictions, allowed characters).

   Your task: Create a Username value object that encapsulates any validation logic.


2. `private double balance;` - why?  Using double for balances is a potential issue because financial values require
   precision and often have specific rules for handling (e.g., rounding, currency formats).

      Your task: Create a Username value object that encapsulates any validation logic.


3. `private List<String> transactionHistory;` - why? Storing transaction history as a List<String> may be too simplistic
    if transactions have multiple attributes (e.g., amount, date, type).

   Your task: Create a Transaction class to encapsulate transaction details.











