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


