# AWS V4 Authentication

**Definition**: AWS Signature Version 4 authentication configuration

**Attributes**:

- `type` (string, Required): Must be `awsv4`
- `aws` (object, Required): AWS V4 configuration
  - `accessKey` (string, Required): AWS access key ID
  - `secretKey` (string, Required): AWS secret access key
  - `region` (string, Required): AWS region (e.g., `us-east-1`)
  - `service` (string, Required): AWS service name (e.g., `execute-api`)
  - `sessionToken` (string, Optional): AWS session token for temporary credentials

**Example**:

```yaml
auth:
  type: awsv4
  aws:
    accessKey: '{{awsAccessKey}}'
    secretKey: '{{awsSecretKey}}'
    region: us-east-1
    service: execute-api
    sessionToken: '{{awsSessionToken}}'
```
