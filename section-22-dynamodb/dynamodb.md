# Overview
DynamoDB is a managed NoSQL database which is distributed & highly horizontal scalable, highly available by replicating across AZ, it can handle millions of requests per second, trillion of row and 100s of TB storage.
Low latency on retrieval. It integrates with IAM for security. It has feature for event driven programming by using DynamoDB Streams. It low cost and has autoscaling capability. It has Standard and Infrequent Access (IA) table class. 

# DynamoDB Basic
#### It mades of Tables
We don't have to create the DB like RDS, instead we create the tables.

#### Tables
- Tables can have infinite number of items or row
- An item can consists of **Primary Key (PK)** and **Attributes** (coloumn)
- 

#### Local Secondary Index (LSI) & Global Secondary Index (GSI)
