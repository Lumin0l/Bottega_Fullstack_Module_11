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
