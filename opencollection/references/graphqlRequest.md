# GraphQL Request

**Definition**: GraphQL request configuration

**Attributes**:

- `info` (GraphQLRequestInfo, Optional): Metadata and documentation for the request
- `graphql` (GraphQLRequestDetails, Optional): GraphQL protocol details
- `runtime` (GraphQLRequestRuntime, Optional): Runtime configuration including variables, scripts, and assertions
- `settings` (GraphQLRequestSettings, Optional): Execution settings
- `docs` (string, Optional): Documentation for this request

**Example**:

```yaml
info:
  name: Get Users Query
  type: graphql

graphql:
  method: POST
  url: '{{baseUrl}}/graphql'
  body:
    query: |
      query GetUsers {
        users {
          id
          name
        }
      }
    variables: '{}'

runtime:
  variables: []
  scripts: []
  assertions: []

settings:
  encodeUrl: true
  timeout: 30000
```

# GraphQL Request Info

**Definition**: GraphQL request metadata and documentation

**Attributes**:

- `name` (string, Optional): The name of the request
- `description` (string, Optional): Description of what the request does
- `type` (string, Optional): The type of request
- `seq` (Sequence, Optional): Sequence number for ordering
- `tags` (array, Optional): Array of tags for categorizing the request

**Example**:

```yaml
info:
  name: Get Users Query
  description: Fetches all users via GraphQL
  type: graphql
  seq: 1
  tags:
    - users
    - graphql
```

# GraphQL Request Details

**Definition**: GraphQL request protocol details

**Attributes**:

- `method` (string, Optional): HTTP method (typically POST)
- `url` (string, Optional): The URL of the GraphQL endpoint
- `headers` (array, Optional): Array of request headers
- `params` (array, Optional): Array of request parameters
- `body` (GraphQLBody | array, Optional): GraphQL query and variables

**GraphQLBody Structure**:

- `query` (string, Required): The GraphQL query string
- `variables` (string | object, Optional): GraphQL variables as JSON string or object
- `operationName` (string, Optional): Name of the operation to execute

**Example**:

```yaml
graphql:
  method: POST
  url: '{{baseUrl}}/graphql'
  headers:
    - name: Authorization
      value: 'Bearer {{token}}'
  body:
    query: |
      query GetUsers($limit: Int) {
        users(limit: $limit) {
          id
          name
          email
        }
      }
    variables: |
      {
        "limit": 10
      }
```

# GraphQL Request Runtime

**Definition**: GraphQL request runtime configuration for variables, scripts, assertions, and authentication

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
    - type: after-response
      code: |
        bru.setVar('users', res.body.data.users);
  assertions:
    - expression: res.status
      operator: equals
      value: '200'
  auth:
    type: bearer
    token: '{{authToken}}'
```

# GraphQL Request Settings

**Definition**: Settings for GraphQL request execution behavior

**Attributes**:

- `encodeUrl` (boolean | string, Optional): Whether to encode the URL
- `timeout` (number | string, Optional): Request timeout in milliseconds
- `followRedirects` (boolean | string, Optional): Whether to follow redirects
- `maxRedirects` (number | string, Optional): Maximum number of redirects to follow

**Example**:

```yaml
settings:
  encodeUrl: true
  timeout: 30000
  followRedirects: true
  maxRedirects:
```
