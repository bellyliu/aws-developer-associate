# Overview
AWS Elastic Beanstalk is to make developer easier to deploy the application without learning the underlying infrastructure to run the application

# Beanstalk Components
- Application: Collection of elastic beanstalk components e.g environments, versions, configurations, etc
- Application Version: Version of our app code
- Environment:
    - Collection of AWS running an application version (only one application at a time) e.g ASG, scaling policy, EC2, Load balancer, SQS, and so on.
    - Tiers: Web environment tier (based on loadbalancer) and Worker environment tier (based on queue)
    - We can create multiple environments (dev, test, prod etc)
<img width="789" alt="image" src="https://github.com/user-attachments/assets/210a548b-2af6-4976-ba59-4d809a9133d8" />

# Supported programming language and platform
Beanstalk supported to deploy various programming language like Go, Python, Ruby etc and it also supported to deploy single/multiple containers.

# Deployment Type
<img width="858" alt="image" src="https://github.com/user-attachments/assets/b6fa1669-2145-42cf-ad4d-891370fd3739" />

# Deployment options for updating the app
- All at once
- Rolling
- Rolling with additional batches
- Immutable
- Blue Green
- Traffic Splitting (Canary)

# CLI
Beanstalk has own a CLI called `eb cli`. It helpfull to managing the EB related things like environment, configuration etc and also make it easier to deploy the application.

# Lifecycle Policy
We could configure the lifecycle policy of EB application to automatically delete the unused/old application based on time or space (when have too many version)

# Extension
We can configure the beanstalk by creating config file (formated in YAML/JSON) inside `.ebextensions/` directory and must be in `.config` file extension. In this file we can configure the envar, add some dependency resources like RDS, elasticache etc. Resources managed by `.ebextensions/` will be deleted if environment deleted.

# Beanstalk Under the hood
It using Cloudformation to configure the beanstalk and provisioning AWS resources defined in `.ebextensions/`

# Cloning
We can clone existing beanstalk environment and it will replicate all the config, dependency resources, envar and so on. After clone we can modify the setting.
**Note: Data inside RDS will not be replicated**
