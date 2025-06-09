# Overview
Event source mapping is a lambda resource that act as bridge between lambda and the stream/queue-based services. It reads data from these services and invoked the function with batches of records. Event source mapping are created and managed within the lambda itself.
Basically it define of how the way lambda function process records from queue/stream-based services.

<img width="506" alt="image" src="https://github.com/user-attachments/assets/c5891b45-cf81-448c-8f26-fd7a56f673c7" />

# Components
- **Event Pollers:** Within an event source mapping, event pollers are resources that actively poll the connected service for new messages. By default, Lambda automatically scales these pollers based on message volume.
- **Batching Behavior:** To process data efficiently, Lambda reads records in batches and invokes the function with a single event containing these records. Batching behavior can be fine-tuned using parameters like BatchSize (maximum number of records in a batch) and MaximumBatchingWindowInSeconds (maximum time to gather records).
- **Synchronous Invocation:** Lambda invokes functions synchronously when processing records from stream and queue-based event sources.
