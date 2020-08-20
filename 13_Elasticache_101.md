## Elasticache 101

* Elasticache is a web service that helps scale an in-memory cache in the cloud.
* Can be used to significantly improve latency and throughput for read-heavy
apps (such as social networking, gaming, media sharing) or compute-intensive
workloads (such as a recommendation engine).
* * Stores critical pieces of data in memory for low-latency access.

#### Types
##### Memcached
  - Elasticache is protocol compliant with Memcached, so popular tools used with
existing Memcached environments will work seamlessly.
  - Elasticache manages Memcached nodes as a pool that can grow and shrink.

###### Use cases:

* Object caching (ie. offload DB).
* Simple model.
* Large cache nodes that require multithreaded performance with utilisation of
multiple cores.
* Scales horizontally.

##### Redis
  - Elasticache manages Redis more as a relational database.
  - Open source key-value store.
  - Can use multi A-Z.

###### Use cases:
* More advanced data types (ie. lists, hashes and sets).
* Sorting and ranking datasets in memory (ie. leaderboards).
* Persistence of key store is important.
* Runs in multi A-Z.

#### Exam tips
If a DB is under a lot of stress, Elasticache is a good choice is DB is
particularly read-heavy and not prone to frequenct changing.
Although Redshift is a good answer if the stress is due to lots of OLAP
transactions being run.
