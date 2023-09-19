# How to Control Flow (if / else)

## Creating Aliases

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

