# Redis

- What is it?

Redis is a database that stores data in memory, instead of on disk. This makes it very fast, but it also means that any data that is not saved to disk will be lost if the Redis server is restarted.

Redis is often used as a cache. This means that it stores copies of data that is also stored in a slower database, such as a relational database. When an application needs to read a piece of data, it can first check the Redis cache to see if the data is already there. If it is, the application can read the data from the cache very quickly. If the data is not in the cache, the application can read it from the slower database and then save a copy of the data to the cache. This way, the next time the application needs to read the data, it can read it from the cache very quickly.

Redis can also be used as a database for applications that need to store real-time data, such as stock prices or social media feeds. Redis is very fast at reading and writing data, so it is ideal for applications that need to process data in real time.

## SET and GET

- SET creates data.
- GET displays data.

```
127.0.0.1:6379> SET page_name 'About us'
OK
127.0.0.1:6379> GET wrong_key
(nil)
127.0.0.1:6379> GET page_name
"About us"
127.0.0.1:6379>
```

### GETSET

- SET overrides values without checks, by typing **GETSET**, you will override the previous value, but it will return what was stored as a sort of measure.

## Key Structure

- In redis we don't have tables, so data is structured in key-value pairs.

- To create those key - value pairs, it is recommended to set an ID first. For example, we want to do a key that tracks likes, we would do it like this:
- `SET 102:like_count 0` -> where 0 is the value we set as a starter.

## Incrementing and Decrementing

- In order to increment that value that initially is 0, we just need to type **INCR** + the key:
- `INCR 102:like_count`
- Same with **DECR**

- If we want to increment or decrement by x number we write **INCRBY** and **DECRBY**.

## Delete

- Just type **DEL** and the key or keys
- `DEL first_name last_name`

## Exists (Boolean checking)

- Typing **EXISTS** + a key will return a 1 if it exists and a 0 if it doesn't.

## Expire

- Redis is inherently ephemeral, so typing **EXPIRE** + a key name + a number of seconds, will delete that key.

## Show keys

### All keys

- **KEY \***

### Keys with some knowledge

- If you don't remember the whole key but you remember some part, how it started, how it ended you can leverage \* like in sql.

## Hashes

- **HSET** They are ways to create collections and complex structured.
- They require the key + the field + the value, so you can do thing like this:

```
127.0.0.1:6379> HSET user name 'Kristine'
(integer) 1
127.0.0.1:6379> HSET user email 'kristine@devcamp.com'
(integer) 1
127.0.0.1:6379> HGET user name
"Kristine"
127.0.0.1:6379> HGET user email
"kristine@devcamp.com"
```
