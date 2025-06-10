# Concurrency & Throttling
Lambda will automatically scale up to 1000 for concurrent execution by default. That limit is per-Region basis. We can ask AWS support to increase the limit.
Each invocation exceed concurrency limit will trigger the "Throttle". We can set **reserved concurrency** at the function level.

Throttle behavior:
- Sync invocation => return ThrottleError - 429
- Async invocation => retry automatically and then to DLQ

#
