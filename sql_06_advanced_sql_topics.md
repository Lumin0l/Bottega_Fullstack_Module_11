# Advanced SQL + Modelling

## Indexes

- They are refference points.

## Database Normalization

- A set of rules stablished as best values.

- Basically to be efficient, so if you create a table with a user, email and address, you don't want the address to be in the same table, because a user can have several addresses.
- In this case, you should make another table with addresses linked to the ids of the users with a foreign key.

- Also related to data types, for example: if a user has a state value as for active-inactive, it should not be stored as a string.
- In that regard, it should also be stated what can be null and what cannot. What gets capitalized...

## Diagram Modeling

- Press ctrl+r and it will open the reverse engineer panel. There you need to navigate and it will create a model of the tables and the relations between them in the style of UML.

- They help visualize the database.
