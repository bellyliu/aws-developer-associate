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


### Local Secondary Index (LSI) & Global Secondary Index (GSI)
