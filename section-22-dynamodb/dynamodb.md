# Overview
DynamoDB is a managed NoSQL database which is distributed & highly horizontal scalable, highly available by replicating across AZ, it can handle millions of requests per second, trillion of row and 100s of TB storage.
Low latency on retrieval. It integrates with IAM for security. It has feature for event driven programming by using DynamoDB Streams. It low cost and has autoscaling capability. It has Standard and Infrequent Access (IA) table class. 

# DynamoDB Basic
### It mades of Tables
We don't have to create the DB like RDS, instead we create the tables.

### Tables
- Tables can have infinite number of items or row
- An item can consists of **Primary Key (PK)** and **Attributes** (coloumn)
- Max. size of an item is 400KB
- Data types supported:
  - Scalar: String, Number, Binary, Boolean, Null
  - Document: List, Map
  - Set: String set, Number set, Binary set
 
### DynamoDB Primary Keys
#### Option 1: Partition Key (HASH)
  - PK must be unique each item
  - PK must be _diverse_ so that data is distributed
<img width="637" alt="image" src="https://github.com/user-attachments/assets/8c399e28-f5eb-45df-b436-c54b87aa1bd0" />

#### Option 2: Partition Key + Sort Key (HASH + RANGE)
  - The combination must be unique each item
  - Data is grouped by PK
<img width="846" alt="image" src="https://github.com/user-attachments/assets/543d3fb1-fdc1-42c5-a9b3-36e88c2dfd14" />

#### Exercise: determine PK
We are building movie database. What is the best PK to maximize data distribution?
- movie_id
- producer_name
- actor_name
- movie_language

Answer: movie_id is the best PK because it has highest cardinality

### DynamoDB Read/Write Capacity Modes
We can control our Table capacity by choosing **Provisioned or On-demand (default) mode**. We only allowed to change the capacity mode once every 24 hours.
- **Provisioned mode**:
  - We specify the number of Read & Write per second.
  - Need to do capacity plan beforehand
  - Pay for provisioned write & read capacity units
  - **Read Capacity Units (RCU):** throughput for read
  - **Write Capacity Units (WCU):** throughput for write
  - It has option to enable auto-scaling of throughput to meet demand
  - Throughput can be exceeed temporarily using _Burst Capacity_
  - If _Burst Capacity_ has been consumed we will get _"ProvisionedThroughputExceededException"_
  - Its then advised to do _exponential backoff_ retry
- **On demand mode:**
  - Read/Write automatically scale up/down with your workload
  - No capacity planning needed
  - Pay for what we use - **more expensive**

### Calculating DynamoDB WCU & RCU
#### WCU
- One WCU = 1 rps for an item up to 1KB
- If the item > 1KB then more WCU consumed
  
**Examples:**
- We write 10 items per second, with item size 2KB
  - We need 10 x (2KB/1KB) = 20 WCUs
- We write 6 items per second, with item size 4.5KB
  - We need 6 x (5KB/1KB) = 30 WCUs (4.5KB rounded up to 5KB)

#### RCU
<img width="375" alt="image" src="https://github.com/user-attachments/assets/f8abea31-9cbb-4cca-88ca-8685c99a7657" />

**Strongly consistent vs Eventually consistent read**
- Eventually consistent (default): If we read right after write, its possible we will get _stale data_ because of replication
- Strongly consistent read: If we read right after write we will get the correct data.
  - Set _ConsistentRead_ parameter to True in API calls (GetItem, BatchGetItem, Query, Scan)
  - It consume twice RCU
- One RCU = 1 strong consistent rps or 2 eventually consistent rps, for an item up to 4KB
- For the item > 4KB then more RCU consumed

**Examples:**
  - 10 strong consistent rps with item size 4KB = 10 x (4KB/4KB) = 10 RCUs
  - 16 eventually consistent rps with item size 12KB = (16/2) x (12KB/4KB) = 24 RCUs
    
### Local Secondary Index (LSI) & Global Secondary Index (GSI)
