# Overview
Lambda is a serverless services in AWS. It means we don't need to provision infra, instead AWS will provision and managing it for us.
When we talk about Lambda, usually we talk about function which is the main program which will be executed during invocation (trigger).
It have so many integration with other AWS services like SNS, Event Bridge, SQS, Kinesis, S3, DynamoDB etc.
Lambda supported in various programming language like python, java, nodejs, C# and golang / rust (with custom run API).
It also supported to deploy container image which implemented Lambda API (search in public ECR galery e.g lambda python or something)

# Serverless in AWS
<img width="408" alt="image" src="https://github.com/user-attachments/assets/d1299ec3-0da1-493c-ab25-dd86f7e6822b" />

# AWS Lambda Integration (main one)
<img width="979" alt="image" src="https://github.com/user-attachments/assets/f7a96aeb-e44a-48a8-b4de-1c3123ef182f" />

# Example use case
### Thumbnail Creation
<img width="1045" alt="image" src="https://github.com/user-attachments/assets/6fce0459-d57d-4637-b6a0-a2306142e7f4" />

### Cronjob
<img width="578" alt="image" src="https://github.com/user-attachments/assets/038a2f1f-72e8-4a7e-99bc-eade6f342b7c" />

# Lambda Invocation Methods
### Sync invocation
- Client will get the result right away
- The error handling must be on client side
<img width="1075" alt="image" src="https://github.com/user-attachments/assets/7b3e3c9c-831b-43d1-b5ef-9ebe862415eb" />

### Async invocation
- Client might not get the result right away because the events will be placed in _Event Queue_ e.g SQS, Kinesis etc
- We can setup _Dead Letter Queue_ (DQL) for failed processing
- Lambda will attepmt to retry on error 3 times. After 1st retry it will wait 1 minute, then 2nd & 3rd retry will wait 2 minutes each.
- Make sure the function code is _idempotent_ in case of retry
<img width="526" alt="image" src="https://github.com/user-attachments/assets/a56f8791-37c0-4e75-a7dc-f99e641b4a18" />
