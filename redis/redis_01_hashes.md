# Hashes

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

## Hash Commands

- **HMSET**, **HDEL**, **HEXISTS**, **HGETALL**, **HINCRBY**, **HKEYS**, **HLEN**, and **HMGET**

- Examples:

```
127.0.0.1:6379> HMSET user:42 name 'Darth' email 'darth@vader.com'
OK
127.0.0.1:6379> HGET user:42 name
"Darth"
127.0.0.1:6379> HMGET user:42 name email
1) "Darth"
2) "darth@vader.com"
127.0.0.1:6379> HGETALL user:42
1) "name"
2) "Darth"
3) "email"
4) "darth@vader.com"
127.0.0.1:6379> HKEYS user:42
1) "name"
2) "email"
127.0.0.1:6379> HEXISTS user:42 email
(integer) 1
127.0.0.1:6379> HEXISTS user:42 altemail
(integer) 0
127.0.0.1:6379> HSET user:42 id 1
(integer) 1
127.0.0.1:6379> HGETALL
(error) ERR wrong number of arguments for 'hgetall' command
127.0.0.1:6379> HGETALL user:42
1) "name"
2) "Darth"
3) "email"
4) "darth@vader.com"
5) "id"
6) "1"
127.0.0.1:6379> HINCRBY user:42 id 123
(integer) 124
127.0.0.1:6379> HGETALL user:42
1) "name"
2) "Darth"
3) "email"
4) "darth@vader.com"
5) "id"
6) "124"
127.0.0.1:6379> HDEL user:42 id
(integer) 1
127.0.0.1:6379> HGETALL user:42
1) "name"
2) "Darth"
3) "email"
4) "darth@vader.com"
127.0.0.1:6379>
127.0.0.1:6379> HLEN user:42
(integer) 2
127.0.0.1:6379> HGETALL user:42
1) "name"
2) "Darth"
3) "email"
4) "darth@vader.com"
127.0.0.1:6379>
```
