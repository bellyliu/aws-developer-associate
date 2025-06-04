# Overview
SQS is a managed queue services from AWS. It has unlimited thoughput and highly scalable, secure, and robust. The data will be encrypted in-flight (https) and at-rest (kms) and the access can be managed by IAM or SQS access policy (usually to grant another AWS service like S3 send data to the SQS).
<img width="992" alt="image" src="https://github.com/user-attachments/assets/6234c998-25cb-4813-8d60-12275a43289b" />

# Type
- Standard queue: at least once delivery ( can have duplicated message )
- FIFO queue:

# Produce & consume the messages
- We can use AWS SDK for both.
- Each message size limited max 256 kb
- Message retention default 4 days, up to max 14 days
- Consumer can receive up to 10 messages at one time. It means the consumer can get up to 10 messages and process it at the same time

# SQS Extended Client
Here is how we overcome the message size limitation (256kb) by send the large data to the S3 instead send it to SQS. The producer will send the small metadata message to the SQS which contain information of the related data inside S3 which need to be proccessed.
<img width="1003" alt="image" src="https://github.com/user-attachments/assets/4b422ac4-f947-4783-893c-51c2f9a99e33" />

# SQS FIFO
- First In First Out = ordering the messages in the queue, so the consumer will process it in order.
- Exactly-once send capability (by removing the duplicates using deduplication ID)
- It using `Message Group ID` to order the messages. It means all the messages at the same group are ordered). `Message Group ID` is mandatory parameter.
- Throughput without batch = 300 msg/s. Throughput with batch 3000 msg/s
<img width="1003" alt="image" src="https://github.com/user-attachments/assets/d47657bc-d56f-40f9-83a9-7ca7c07eeb7d" />

### How FIFO Deduplication works
The FIFO will deduplicate the message in the interval of 5 mins. So within 5 minutes range, if any message body has the same `SHA-256` hash then it will be rejected
<img width="795" alt="image" src="https://github.com/user-attachments/assets/14defba4-4f7a-4335-b642-6f50e4f9b1dd" />
- Deduplication methods:
   - content-based: by checking the `SHA-256`
   - providing the `Message Deduplication ID`

### FIFO - Messages Grouping
If we send messages with same `MessageGroupID` into FIFO then we can only have 1 consumer to process those messages and all the messages are in order.
So different `MessageGroupID` will be processed by another consumer.

**Note: cross group ordering isn't guaranteed**
<img width="741" alt="image" src="https://github.com/user-attachments/assets/a5905123-4922-412b-a2a4-a1b45a8e8171" />
