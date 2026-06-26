# Environments

**Definition**: Defines environment configurations for the collection

**Attributes**:

- `name` (string, Required): Name of the environment
- `variables` (object, Required): Key-value pairs of environment variables
- `description` (string, Optional): Description of the environment

**Example**:

```yaml
environments:
  - name: development
    description: Development environment
    variables:
      baseUrl: 'https://dev-api.example.com'
      authToken: 'dev-token-123'
      timeout: 30000

  - name: production
    description: Production environment
    variables:
      baseUrl: 'https://api.example.com'
      authToken: 'prod-token-456'
      timeout: 10000

  - name: staging
    description: Staging environment
    variables:
      baseUrl: 'https://staging-api.example.com'
      authToken: 'staging-token-789'
      timeout: 20000
```
