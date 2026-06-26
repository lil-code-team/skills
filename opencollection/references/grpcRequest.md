# gRPC Request

**Definition**: gRPC request configuration

**Attributes**:

- `info` (GRPCRequestInfo, Optional): Metadata and documentation for the request
- `grpc` (GRPCRequestDetails, Optional): gRPC protocol details
- `runtime` (GRPCRequestRuntime, Optional): Runtime configuration including variables, scripts, and assertions
- `docs` (string, Optional): Documentation for this request

**Example**:

```yaml
info:
  name: Get User
  type: grpc
  description: Fetches a user by ID via gRPC

grpc:
  host: '{{grpcHost}}'
  port: 50051
  method: GetUser
  service: UserService
  proto: |
    syntax = "proto3";
    service UserService {
      rpc GetUser (UserRequest) returns (UserResponse);
    }
  body:
    id: '{{userId}}'

runtime:
  variables: []
  assertions: []
  scripts: []
```

# gRPC Request Info

**Definition**: gRPC request metadata and documentation

**Attributes**:

- `name` (string, Optional): The name of the request
- `description` (Description, Optional): Description of what the request does
- `type` (string, Optional): The type of request
- `seq` (Sequence, Optional): Sequence number for ordering
- `tags` (array, Optional): Array of tags for categorizing the request

**Example**:

```yaml
info:
  name: Get User
  description: Fetches a user by ID via gRPC
  type: grpc
  seq: 1
  tags:
    - users
    - grpc
```

# gRPC Request Details

**Definition**: gRPC request protocol details

**Attributes**:

- `host` (string, Optional): gRPC server hostname or IP
- `port` (number, Optional): gRPC server port
- `method` (string, Optional): gRPC method name
- `service` (string, Optional): gRPC service name
- `proto` (string, Optional): Protocol buffer definition
- `body` (object, Optional): Request payload
- `metadata` (object, Optional): gRPC metadata headers

**Example**:

```yaml
grpc:
  host: localhost
  port: 50051
  method: GetUser
  service: UserService
  proto: |
    syntax = "proto3";
    service UserService {
      rpc GetUser (UserRequest) returns (UserResponse);
    }
  body:
    id: '{{userId}}'
  metadata:
    authorization: 'Bearer {{token}}'
```

# gRPC Request Runtime

**Definition**: gRPC request runtime configuration for variables, scripts, and assertions

**Attributes**:

- `variables` (array, Optional): Array of runtime variables
- `scripts` (Scripts, Optional): Scripts to execute at different lifecycle stages
- `assertions` (array, Optional): Array of assertions for response validation
- `auth` (Auth, Optional): Authentication configuration

**Example**:

```yaml
runtime:
  variables:
    - name: userId
      value: '123'
  scripts:
    - type: before-request
      code: |
        bru.setVar('timestamp', Date.now());
  assertions:
    - expression: res.status
      operator: equals
      value: '0'
  auth:
    type: bearer
    token: '{{authToken}}'
```
