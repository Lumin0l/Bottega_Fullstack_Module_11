# How to Control Flow (if / else)

## Creating Aliases

### Aliases for columns

- It can be useful to create aliases for the different column names so they don't get the sql style ones when viewing / exporting:

```
SELECT
addresses_street_one AS 'Street',
addresses_street_two AS 'Street 2',
addresses_city AS 'City',
addresses_state AS 'State',
addresses_postal_code AS 'Postal Code'
FROM addresses;
```

### Aliases for Tables

- Sometimes it will be useful to get aliases for tables when importing data from several different ones:
- Just write "FROM "New-Name" and then use it as a method: "New-Name.data"

```
ELECT g.guides_title, g.guides_revenue
FROM guides g
WHERE g.guides_revenue > 600;
```

## Case Statements

- We can't apply case statements as usual (with if, else) but we can do it.

- Let's say we want to get the info on the guides based on the money they made, and we want to get the info based on whether they made a lot or not. We can cast the ones that made more than 1000 so they are returned as 'best sellers', the ones that made less than 600 as 'Not Displayed' and the rest as 'average'. We would do it like this:

```
SELECT
  guides_title,
  CASE
    WHEN guides_revenue > 1000 THEN 'Best Seller'
    WHEN guides_revenue < 600  THEN 'Not Displayed'
    ELSE 'Average Sellers'
  END AS 'status'
FROM guides;
```
