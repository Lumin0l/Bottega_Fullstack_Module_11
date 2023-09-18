# SQL Intro, Syntax and Uses

The syntax is fairly symple, by convention the commands are written in caps and then the parameters in lowercase. Full scripts are terminated by ";".

## Create a Database:

- **CREATE**: `CREATE DATABASE mydatabase;`

## Select DataBase where to work:

- Will select the particular database or schema where to work.
- **Use**: `USE devcamp_sql_course_schema;`

## Create Table inside database

- **CREATE TABLE**: `CREATE TABLE users`
- Then we can introduce the parameters that will conform the table and specify rules, like vaslue of id and if it increments automatically. All in parentheses:

```
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL
);
```

## Adding Elements to Table

- Once we have created a dabase and a table with different parameters, we can start introducing stuff in it. For that, you need to select database, table and then specify parameters to introduce.
- **INSERT INTO** + **VALUES**:

```
INSERT INTO users(users_name, users_email)
VALUES ("Kristine", 'kristine@test.com');
```

## Query all table

- Just to visualize the table contents.
- To **query all** we do: `SELECT *`

- This is not a very good practice, because there might be millions of rows and columns. To query select elements, name the database, the table and the parameters you wanna get:
- **SELECT**:

```
USE devcamp_sql_course_schema;

SELECT users_name, users_email
FROM users;
```

### Filtering Queries:

- To filter elemts **by content** we use:
- **where**, **and**, **or**:

- To filter by name:

```
SELECT *
FROM users
WHERE users_email = 'kristine@test.com'
OR users_email = 'jordan@test.com';
```

- Filter by address parameter using and:

```
SELECT *
FROM addresses
WHERE addresses_state = 'NY'
AND addresses_city = 'Manhattan'
AND addresses_users_id = 1;
```

### Limit query output

- To limit the ammount of entries that the query returns you can use:
- **LIMIT**:

```
SELECT *
FROM users
LIMIT 10;
```

- You can also offset (start from a different point, like "start from the fifth position"):

```
SELECT *
FROM users
LIMIT 5, 10;
```

### Find Unique Values (Not duplicates)

- If you want to find elements that are not repeated, you need to to specify the parameter (the "row").
- **SELECT distinct**:

```
SELECT distinct guides_title, guides_users_id, guides_revenue
FROM guides;
```

### Order queries

- To organize the order in which the elements come there are a few keywords. Bear in mind that the default is whatever the parameter is set as, normally alphanumeric. If you want a specific value, you need to cast it.
- **ORDER BY** + **ASC** || **DESC**:

```
SELECT guides_title
FROM guides
ORDER BY guides_title DESC;

SELECT guides_title
FROM guides
ORDER BY guides_title ASC;
```

- To cast: **CAST**:

```
SELECT guides_revenue, guides_title
FROM guides
ORDER BY CAST(guides_revenue AS UNSIGNED) DESC;
```

### Order by Range (of the vakue)

- When dealing with numbers we can filter by value range:
  **BETWEEN** + **AND**:

```
SELECT *
FROM guides
WHERE guides_revenue BETWEEN 1000 AND 5000;
```

- We can also exclude ranges with **NOT BETWEEN**:

```
SELECT *
FROM guides
WHERE guides_revenue NOT BETWEEN 600 AND 1200;
```

### Wildcard search (string value A.K.A.: ctrl+f)

- We specify the string with **%**. It is like "\*" in shell, so if we want to filter "all that ends in .js, we do "%.js". So the options are:

- Keyword: **LIKE**.

- Full exact word / sentence: **%word%**.
- Starts with: **word%**.
- Ends with: **%word**.

```
SELECT *
FROM guides
WHERE guides_title LIKE '%My%';
```

- We can also exclude with **NOT LIKE**:

```
SELECT *
FROM guides
WHERE guides_title NOT LIKE '%My%';
```

## Edit Records:

- To update and edit the existing content of tables we do:
- **UPDATE** + **SET**:

```
UPDATE users
SET users_email = 'update@test.com'
WHERE users_id = 2;
```

- With **UPDATE** we give the instruction we want the script to perform, and with **SET** we pass the value we want to set.
- As you can see it's a bit counterintuitive. First we state the new value and then using **WHERE** we state where we want to stick it.

- We can also use **and** and **or** to specify more where the value will go:

```
UPDATE guides
SET guides_title = 'Something Else'
WHERE guides_title = 'Another Post'
AND guides_users_id = 2;
```

## Create a History (create ctrl+z functionality)

- In mySQL changes are permanent by default, so a good practice to protect yourself from errors when adding or changing values is the use of **BEGIN** and **ROLLBACK**.
- With **BEGIN** we state the point where the actions will start to be recorded, and by typing **ROLLBACK** we go back to the original point.

```
BEGIN;
UPDATE guides
SET guides_title = 'Oops'
WHERE guides_users_id = 1;

SELECT *
FROM guides;

ROLLBACK;
```

## DELETE

- **DELETE**. Same as with updating, recommended to use rollback:

```
SELECT *

BEGIN;
DELETE FROM users
WHERE users_id = 199;

ROLLBACK;
```
