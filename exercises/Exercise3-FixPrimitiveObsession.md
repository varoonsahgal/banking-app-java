# Refactoring to fix the Primitive Obsession code smell

Now, you've identified the candidates for primitive obsession, it's time to get to work and fix them!


There are 3 candidates for primitive obsession that you now need to fix:

1. `private String username;` - why?  because using String for usernames can be considered a form of primitive obsession if
   usernames have specific rules or behaviors associated with them (e.g., length restrictions, allowed characters).

   Your task: Create a Username value object that encapsulates any validation logic.


2. `private double balance;` - why?  Using double for balances is a potential issue because financial values require
   precision and often have specific rules for handling (e.g., rounding, currency formats).

      Your task: Create a Balance value object that encapsulates any validation logic.


3. `private List<String> transactionHistory;` - why? Storing transaction history as a List<String> may be too simplistic
    if transactions have multiple attributes (e.g., amount, date, type).

   Your task: Create a Transaction class to encapsulate transaction details.


   You will need about 45 minutes for this exercise.
