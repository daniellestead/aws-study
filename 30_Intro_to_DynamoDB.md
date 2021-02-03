## DynamoDB

- Fast and flexible NoSQL database
- Good for applications that need consistent, single digit millisecond latency at any scale
- Flexible data model and reliable performance
- Good for mobile, web, gaming, ad-tech, IoT etc apps
- Dont need to define schema upfront
- Serverless!
- Integrates well with Lambda
- Stored on SSD
- Spread across 3 geographically distinct data centres
- Made up of tables, items (a row of data in a table) and attributes (a column of data in a table)
- Supports key-value (key=name of data, value=data) and document (document=JSON,HTML or XML) data structures
- Access is managed using AWS IAM, which also allows you to create temporary keys and special *conditions* to restrict users to only access their own records (eg. gamer accessing high scores across the games they play, but can't see other peoples high scores)

#### Eventual consistent read (default)
Consistency across all copies of data is usually reached within a second. Repeating a read after a short time should return the updated data. (Best read performance)

#### Strongly consistent read
Returns a result that reflects all writes that received a successful response prior to the read.

### Primary keys
Two types:
1. Partition key: A unique attribute (such as ID). The value of the partition key is input to an internal hash function which determines the partition or physical location on which the data is stored. **If you are using partition key as your primary key then** *no two items* **can have the same partition key**
2. Composite key: Partition key + sort key. For example the same user posting multiple times to the same forum would have a user ID as the partition key and the timestamp of the post as the sort key. 2 items can have the same partition key, as long as they have a different sort key. All items with the same partition key are stored together and the sorted according to the sort key.  This **allows you to store multiple items with the same partition key**.

### Exam tips
- Amazon DynamoDB is a low latency NoSQL database
- Consists of Tables, Items and Attributes
- Supports both document and key-value data models
- Supported document formats are JSON, HTML & XML
- 2 types of primary key (partition key & composite key)
- 2 consistency models
- Access is controlled with IAM policies
- The `dynamodb:LeadingKeys` condition parameter allows users to only access the items where the partition key matches the user ID.
