# Kinesis Data Stream
For real time streaming data. It able to retain the data up to 365 days. It have 2 mode: provisioned throughput & on-demand. It has feature to reply data from consumer side.
<img width="1061" alt="image" src="https://github.com/user-attachments/assets/005e021d-61f3-4b7e-b2c7-d881a856a99a" />

# Firehose
- For near real-time streaming data. It able to keep streaming data in buffer for certain period or until it reach buffer size then it will flush the data to the destination. It has feature to transform data in-flight by utilizing Lambda or built-in transofrmer.
- No data retention here
- Serverless autocaling
- Doesn't support data replay
<img width="1142" alt="image" src="https://github.com/user-attachments/assets/08d75ce5-8e57-41bf-b061-cb8b4aaa87b8" />
