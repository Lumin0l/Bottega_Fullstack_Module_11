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
