# Identifying the Primitive Obsession code smell


Your first goal is to identify primitive obsession in your banking application code. You should look out for the following signs:

- Usage of Primitive Types to Represent Domain Concepts
Example: Using String to represent an email address, phone number, or social security number.
Indicator: Repeated code to validate or manipulate these strings.

- Lack of Domain-Specific Types
Example: Using int, double, or String for concepts that have specific rules or behaviors, like money, coordinates, or dates.
Indicator: You see the same validation or business logic spread across multiple methods.

- It's an unconstrained type - if there's no boundaries on possible values and it's NOT a local variable

Once you identify a candidate for primitive obsession, take note.










