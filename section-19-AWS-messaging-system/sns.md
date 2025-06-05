# Overview
Its a Pub/Sub service to broadcast a messages to multiple destination
<img width="1031" alt="image" src="https://github.com/user-attachments/assets/7b8f9f38-8370-466b-98b4-8b1fa5373bf5" />

# How it works
- One producer only send messages to a SNS topic and SNS will send it to the one or more subsribers
- Up to 12.500.000 subsriber per one topic
- Limit 100.000 topics
- **Data isn't presistent in SNS**
<img width="844" alt="image" src="https://github.com/user-attachments/assets/9fae73c9-cafd-467d-a527-fe5428141ba5" />

# Security
- Inflight encryption (https)
- At-rest encryption KMS 
- Client-side encryption
- IAM
- SNS access policy

# SNS + SQS: Fan Out
- Data will be persistent in SQS
- Cross-region SQS delivery
<img width="736" alt="image" src="https://github.com/user-attachments/assets/87be654a-65b2-4253-8487-752a9beebb9b" />

# SNS FIFO
- Limited by SNS FIFO trhoughput similar with SQS FIFO
<img width="976" alt="image" src="https://github.com/user-attachments/assets/c98b44ec-16b4-4e43-8660-303c73c2daeb" />

# SNS FIFO + SQS FIFO
- In case we need fan out + ordering + deduplication
<img width="711" alt="image" src="https://github.com/user-attachments/assets/0a06d46f-ace9-44f1-b17b-7392d9a5a302" />

# SNS Filtering
<img width="980" alt="image" src="https://github.com/user-attachments/assets/91033073-669f-405e-b267-e07126d040aa" />

