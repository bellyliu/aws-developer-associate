# Overview
AWS Cloudformation is a tool to provision and managing AWS resources using code, or we could say Infrastructure as a code. We can write in JSON/YAML.

# Template
Cloudformation template is a template file which can be reused to provision or managing the AWS resources. It can containing the variables and logic.

# How it works
- Template must be uploaded to S3
- To update template, we can't edit the previous one. We have to reupload the new version of template
- Stacks are identified by name
- Deleting Stack will delete every single resources that was created by Cloudformation
<img width="1019" alt="image" src="https://github.com/user-attachments/assets/87e3028f-c38c-4140-8767-1e49a290ac6d" />

# Deploying Cloudformation Templates
- Manual way
Edit the template in Infrastructure editor or code editor, then use Cloudformation console to upload template and input the parameters etc.
<img width="336" alt="image" src="https://github.com/user-attachments/assets/04fdeba8-b3d3-419a-83f6-d31bf3af2688" />

- Automatic way
Create the template in code editor and then use the AWS CLI to deploy the template or using CD tools.
<img width="336" alt="image" src="https://github.com/user-attachments/assets/f3cc11f6-1fab-4bd3-a53d-9e7c9e7f286e" />

# Template building blocks
### Template Components
- AWSTemplateFormatVersion
- Description
- Resources
- Parameters
- Mapping
- Outputs
- Conditionals
  
### Template Helper
- References
- Functions
