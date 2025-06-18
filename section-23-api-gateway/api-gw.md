# Types
- HTTP API: Cheapest but has limited features e.g only support HTTP Proxy & Private integration which mean both of them not supporting custom data mapping and not supported resource base policy
- REST API: Flexible and supported data mapping. Not supported Oauth2.0 and Open ID connect
- Socket Web API: For 2 way communication, which mean server also can push data to the client side without requested first by client e.g for chat apps etc.

# Security
- IAM
  - Use IAM user/role for within same AWS account, + resource based policy for cross AWS account
  - Handle authentication & authorization
  - Leverage SignatureV4
- Custom Authorizer
  - We have to setup lambda to handle the authentication + authorization
  - Greate for 3rd party tokens
- Cognito User Pool
  - We manage our own user pool
  - No need to write any custom code
  - Must implement authorization in the backend
