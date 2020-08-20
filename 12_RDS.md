## Backups, Multi A-Z and Read Replicas

#### Back up types
* Automated backups
  - Allow you to backup your database within a retention period of 1 - 35 days.
  - Stores daily snapshots and transactional logs throughout the day.
  - Enabled by default.
  - Backup data is stored on S3 with free storage space equal to the size of the
database.
  - Storage I/O may be suspended with data is being backed up and this may cause
some latency issues.

* DB backups
  - Snapshot taken manually.

#### Restoring databases
When you restore a DB, the new DB will have a different DNS endpoint.

#### Encryption
Encryption at rest is enabled for all RDS types listed. It is done using AWS KMS
(Key Management Service). **Every time you create a copy of a snapshot you can encrypt that
data, so restoring the DB instance encrypts your DB**.

#### Multi A-Z
*Synchronous*

If we have some EC2 instances behind an ELB that connect to an RDS, there is a
backup RDS with a different DNS address in *another availability zone*. If your DB fails, AWS automatically
switches to the other RDS.

**Multi A-Z is for disaster recovery only**

If you want performance improvement...

#### Read replicas
*Asynchronous*

When writing to a DB, we can have up to 5 read replicas. This is good if your DB
has a large amount of read traffic, so you can scale out by pointing your EC2
instances to the replicas. You can have read
replicas of read replicas, although this will cause some latency. These are
**read-only** however.

* Must have automatic backups turned on to deploy a read replica.
* Each read replica has it's own DNS endpoint.
* You can have read replicas that have multi A-Z.
* You can create read replicas of multi A-Z source databases.
* Read replicas can be promoted to be their own database, although this breaks the
replication.
* You can have a read replica in a second region.
