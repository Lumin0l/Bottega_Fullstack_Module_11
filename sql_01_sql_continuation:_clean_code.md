# Continuation of the SQL Syntax

## Cleaning multiple specific queries

- Parentheses with all the parameters:

```
SELECT *
FROM addresses
WHERE addresses_city = 'Queens'
OR addresses_city = 'Manhattan';

-- Is the same as:

SELECT *
FROM addresses
WHERE addresses_city IN ('Queens', 'Manhattan');
```

## Subqueries

- You can add more specifity to the queries by attaching more queries inside parentheses.
- In this case we will try to get the name and value of the element with the largest number (after casting unsigned) inside an element:

```
SELECT guides_title, guides_revenue
FROM guides
WHERE guides_revenue = (
  SELECT MAX(CAST(guides_revenue AS UNSIGNED))
  FROM guides
);
```

- Another example to retrieve all addresses from the different cities contained in a state:

```
SELECT *
FROM addresses
WHERE addresses_city IN (
  SELECT addresses_city
  FROM addresses
  WHERE addresses_state = 'NY'
);
```

- We can also use it to dynamically get values. Let's say we want to transfer a recently created element "jon" into another table and insert some extra info with it, but we don't know it's id. We can do this:

```
INSERT INTO guides(guides_revenue, guides_title, guides_users_id, guides_qty)
VALUES(
  500,
  'Guide by Jon',
  (SELECT users_id FROM users WHERE users_name = 'Jon' LIMIT 1),
  300);
```
