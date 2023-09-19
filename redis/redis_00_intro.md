# Redis

- What is it?

Redis is a database that stores data in memory, instead of on disk. This makes it very fast, but it also means that any data that is not saved to disk will be lost if the Redis server is restarted.

Redis is often used as a cache. This means that it stores copies of data that is also stored in a slower database, such as a relational database. When an application needs to read a piece of data, it can first check the Redis cache to see if the data is already there. If it is, the application can read the data from the cache very quickly. If the data is not in the cache, the application can read it from the slower database and then save a copy of the data to the cache. This way, the next time the application needs to read the data, it can read it from the cache very quickly.

Redis can also be used as a database for applications that need to store real-time data, such as stock prices or social media feeds. Redis is very fast at reading and writing data, so it is ideal for applications that need to process data in real time.
