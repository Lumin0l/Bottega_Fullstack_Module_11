# Functions in mySQL

## How to change the value of an element

- Casting only changes the value for that particular iteration, but sometimes you'll need to change the value itself.

- It's done from the "edit" button of the GUI. (lame)

## Aggregate Functions

- Functions that aggregate data (add or collect) and give a single value back.

- Examples we've seen are **MIN**, **MAX**. They take looots of values, but return only 1, either the smallest or the biggest.

- We also have:
- **AVG**: average
- **SUM**: sum elements
- **COUNT**: count how many elements

- Remember you need to use **SELECT** before:

```
SELECT MIN(guides_revenue)
FROM guides;

SELECT MAX(guides_revenue)
FROM guides;

SELECT AVG(guides_revenue)
FROM guides;

SELECT SUM(guides_revenue)
FROM guides;

SELECT COUNT(*)
FROM users;
```

## Group By

- It will allow us to create summary reports right In the SQL.

- Let's say we have several addresses saved into a list of states and we want to know how many addresses we have in each states. We would do this:

```
SELECT addresses_state, COUNT(addresses_state)
FROM addresses
GROUP BY addresses_state;
```

- If we had some guides that we sold to some users, and we wanted to know how much money each user has generated (from all guides) we would do this:
```
SELECT guides_users_id, SUM(guides_revenue)
FROM guides
GROUP BY guides_users_id;
```

## Formulas and Math

- We can do math and calculations in mySQL, like let's say we want to check the ammount of money each guide has done:
```
SELECT
guides_title,
guides_revenue,
guides_qty,
guides_revenue / guides_qty
FROM guides;
```

