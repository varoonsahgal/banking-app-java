# Identifying and Refactoring the Long Methods code smell


### 1. Identify Long Methods

Clone down the sample banking application.  Play the game and become familiar with it - you can refer to the instructions in the README.  

Then, look at the BankingApplication.java file and identify any methods that qualify as **long methods**.

Some things to consider when determining if a method is long:

- Multiple Responsibilities
Violation of Single Responsibility Principle (SRP): The method handles more than one responsibility or concern. For example, it might handle data retrieval, processing, and formatting all within the same method.

- Excessive Length of Code
Too Many Lines of Code: The method contains a large number of lines, making it difficult to read and understand.
Complex Logic: The method contains complex algorithms or business logic that could be broken down into simpler, smaller methods.

- Nested Structures
Deeply Nested Loops and Conditionals: The method has multiple levels of nested loops or conditional statements, which can make the code difficult to follow.

- Repeated Code
Code Duplication: The method contains duplicated code that could be extracted into separate methods or utility functions.

- Comprehension
Is it difficult to understand what's going on with the method? If so, it's a long method!


### 2. Refactor using Extract Method

Utilize the automated Extract Method (CMD+OPTION+M on the Mac) in IntelliJ to break down long methods and fix the code smell.  Give your new method(s) meaningful names - remember that readability is huge.






