# Relational Queries

- SQL was even created, and that is how to deal with relational data. SQL Is a relational database management system. That means that each one of our tables can reference another table.

## Multiple conditionals

- We can keep stacking conditionals to get data:

```

SELECT *
FROM guides g
JOIN users u
ON g.guides_users_id = u.users_id
WHERE g.guides_revenue > 700
AND u.users_name = 'Tiffany'
OR u.users_name = 'Kristine';
```

## Inner Joins

- This is the true strenght of SQL, that it allows to join different tables.

### INNER JOIN

- Let's join next to each other 2 tables. Let's say we want to join out users table with our guides table to know exactly who wrote what:

```
SELECT *
FROM guides
INNER JOIN users
ON guides.guides_users_id = users.users_id;
```

- Since this is the most usual type of join, you can just type **JOIN** and it will do this:

```
SELECT *
FROM guides
JOIN users
ON guides.guides_users_id = users.users_id;
```

- **Other Example**: so, we want to join into the user and guide id, the guide, the title, the revenue and the email. With aliases so it's pretty, and orgereded in a descending manner:

```
SELECT
g.guides_title,
g.guides_revenue,
u.users_name,
u.users_email
FROM guides g
JOIN users u
ON g.guides_users_id = u.users_id
ORDER BY g.guides_revenue DESC;
```

### Joining More than 2 Tables:

- The one requirement you're going to have with this is that each table has to be related to one of the other tables, and have that foreign key reference relationship. Then you can Join all number of tables:

```
SELECT *
FROM users u
JOIN guides g
ON g.guides_users_id = u.users_id
JOIN addresses a
ON a.addresses_users_id = u.users_id
ORDER BY g.guides_revenue DESC;
```

## Outer Joins

- In inner joins there has to be a relation between the table, in our case: the id, both the user had id and the guides had user_id that was the same. If we do an Inner Join with elements that don't have shared relations, it won't show it.

- For that we use **RIGHT JOIN** and **LEFT JOIN**. With those Joins we will add any other value, the RIGHT and LEFT will put the focal point in the first or the second table to attach:

```
-- Right Outer Join
SELECT *
FROM guides g
RIGHT JOIN users u
ON g.guides_users_id = u.users_id;

-- Left Outer Join
SELECT *
FROM guides g
LEFT JOIN users u
ON g.guides_users_id = u.users_id;
```

- In the left join we're saying that I want guides to be the focal point
- In the right we're saying that I want users to be the focal point
