# How Amazon Route 53 uses bias to route traffic

Here's the formula that Amazon Route 53 uses to determine how to route traffic:

**Bias:**
- `Biased distance = actual distance * [1 - (bias/100)]`

When the value of the bias is positive, Route 53 treats the source of a DNS query and the resource that you specify in a geoproximity record (such as an EC2 instance in an AWS Region) as if they were closer together than they really are. For example, suppose you have the following geoproximity records:

- A record for web server A, which has a positive bias of 50
- A record for web server B, which has no bias

When a geoproximity record has a positive bias of 50, Route 53 halves the distance between the source of a query and the resource for that record. Then Route 53 calculates which resource is closer to the source of the query. Suppose web server A is 150 kilometers from the source of a query and web server B is 100 kilometers from the source of the query. If neither record had a bias, Route 53 would route the query to web server B because it's closer. However, because the record for web server A has a positive bias of 50, Route 53 treats web server A as if it's 75 kilometers from the source of the query. As a result, Route 53 routes the query to web server A.

Here's the calculation for a positive bias of 50:

```
Bias = 50
Biased distance = actual distance * [1 - (bias/100)]

Biased distance = 150 kilometers * [1 - (50/100)]
Biased distance = 150 kilometers * (1 - .50)
Biased distance = 150 kilometers * (.50)
Biased distance = 75 kilometers
```
