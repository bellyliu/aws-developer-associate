# Overview 
Managed service by AWS which works like Jaeger for tracing.
<img width="768" alt="image" src="https://github.com/user-attachments/assets/2f42ca4e-bc4b-444d-9bd8-75e98ef178ba" />

# How to use it
1. Our code must using AWS X-Ray SDK. So we will have little code modification
2. Install AWS X-Ray daemon (EC2, ECS, EKS or on prem) or enable AWS X-Ray integration (Lambda, Beanstalk or any AWS services)
3. Make sure to attach proper IAM permission for the daemon.
<img width="276" alt="image" src="https://github.com/user-attachments/assets/290794db-803e-4d62-a0ad-c947d0d3056d" />

# Beanstalk + X-Ray integration
We can run the daemon in Beanstalk by enable it in Beanstalk Console or by config in `.ebextenstions/xray-daemon.config`
```
options_settings:
  aws:elasticbeanstalk:xray:
    XRayEnabled: true
```

X-Ray damon not supported for Multicontainer Docker beanstalk

# ECS + X-Ray integration
<img width="1047" alt="image" src="https://github.com/user-attachments/assets/71c33ec3-5f4a-4c64-87de-c5175f476165" />

# AWS Distro for OpenTelemetry
Its working like the opensource OTEL agent collector which able to collect metrics, logs & traces and send them to multiple destinations (no vendor lock-in). It has feature for `auto-instrumentstion` which means we don't need to modify our code to send telemetry data, instead we just need to  install the Agent. It also collect the metadata from our AWS services. It can be used by EC2, EKS, ECS, Lambda etc.
<img width="1047" alt="image" src="https://github.com/user-attachments/assets/2a63ba1f-85cb-4428-b79a-d047e9a6dba7" />
