# Relational Database in AWS
AWS offer managed service to host DB servers. AWS will managed the underlying infrastructure of the DB servers. It has option to create RDS for Postgresql, Mysql, Oracle, MariaDB, and MS SQL server.

# Amazon Aurora
Amazon Aurora is an AWS propiertary DB which has better performance. It compatible with Mysql & Postgresql and has serverless deployment option.

# Elasticache
Its a managed cache server which has option to deploy Redis, Memcached, and Valkey.

# Scaling
All of those services has option to enable the HA by using Muli-AZ deployment, create Read-replica in different AZ, or even cross-zone Read-replica

# Caching Strategy
### Lazy Loading
<img width="356" alt="image" src="https://github.com/user-attachments/assets/533f1332-9d0d-4423-9732-35fbd19f1744" />

**How it works:**
1. When the app need to read from DB, it will read from Cache first
2. If _cache hit_ then data returned, and the app will not proceeding read to the DB
3. If _cache miss_ then app will proceeding read to the DB and app will populating the Cache with data from DB

**Advantages**
- The cache contains only data that the application actually requests, which helps keep the cache size cost-effective.
- Implementing this approach is straightforward and produces immediate performance gains, whether you use an application framework that encapsulates lazy caching or your own custom application logic.

**Disadvantage**
- A disadvantage when using cache-aside as the only caching pattern is that because the data is loaded into the cache only after a cache miss, some overhead is added to the initial response time because additional roundtrips to the cache and database are needed.


### Write-trough
<img width="303" alt="image" src="https://github.com/user-attachments/assets/904a3450-708e-490e-b5eb-b1933ed7aa82" />

**How it works**

A write-through cache reverses the order of how the cache is populated. Instead of lazy-loading the data in the cache after a cache miss, the cache is proactively updated immediately following the primary database update. The fundamental data retrieval logic can be summarized as follows:
- The application, batch, or backend process updates the primary database.
- Immediately afterward, the data is also updated in the cache.

The write-through pattern is almost always implemented along with lazy loading. If the application gets a cache miss because the data is not present or has expired, the lazy loading pattern is performed to update the cache.

**Advantages**
- Because the cache is up-to-date with the primary database, there is a much greater likelihood that the data will be found in the cache. This, in turn, results in better overall application performance and user experience.
- The performance of your database is optimal because fewer database reads are performed.

**Disadvantage**

A disadvantage of the write-through approach is that infrequently-requested data is also written to the cache, resulting in a larger and more expensive cache.
A proper caching strategy includes effective use of both write-through and lazy loading of your data and setting an appropriate expiration for the data to keep it relevant and lean.
