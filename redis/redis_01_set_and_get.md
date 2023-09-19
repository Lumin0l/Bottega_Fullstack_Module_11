# SET and GET

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
