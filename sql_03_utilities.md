# Utilities

## Turn Safe Mode Off

- In some cases we would want to turn it off. This way, sql will only provide warnings, but it won't stop actions from happening.
- It is as easy as this: `SET SQL_SAFE_UPDATES = 0`

## Create Random Numbers

- With **RAND**:

```
BEGIN;
UPDATE guides
SET guides_qty = RAND()*1000;
```

## Cast Names to Rows

- You can name rows to create name -> value pairs. Those pairs will remain when exported so it's a good practice:
- Example:

```
SELECT 'Email:', users_email, 'Name:', users_name
FROM users;
```

## Coalesce

- The **COALESCE** Key will allow us to count the elements inside a table like **COUNT**, but filtering data.

- Usefull when we're counting more than one element, because if we say count a users addresses and guides, it will give duplicate values, because it will add 1 for each, so if in a same gude the user has an address, it will return 2.

- Example:

```
SELECT
  u.users_email AS 'Email',
  COALESCE(g.guide_count, 0) AS guide_count,
  COALESCE(a.address_count, 0) AS address_count
FROM users u
```

- As a massive example, here is a query that counts the addresses and guides separatelly from 2 different tables and join it all in a single return:

```
SELECT
  u.users_email AS 'Email',
  COALESCE(g.guide_count, 0) AS guide_count,
  COALESCE(a.address_count, 0) AS address_count
FROM users u
  LEFT JOIN (
    SELECT COUNT(*) AS guide_count, guides_users_id
    FROM guides
    GROUP BY guides_users_id
  ) AS g
  ON g.guides_users_id = u.users_id
  LEFT JOIN (
    SELECT COUNT(*) AS address_count, addresses_users_id
    FROM addresses
    GROUP BY addresses_users_id
  ) AS a
  ON a.addresses_users_id = u.users_id
ORDER BY u.users_email;
```
