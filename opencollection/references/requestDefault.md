# Request Defaults

**Definition**: Default configuration applied to all requests in the collection

**Attributes**:

- `headers` (array, Optional): Default headers to add to all requests
- `params` (array, Optional): Default parameters to add to all requests
- `auth` (Auth, Optional): Default authentication for all requests
- `settings` (Settings, Optional): Default settings for all requests

**Example**:

```yaml
requestDefaults:
  headers:
    - name: Accept
      value: application/json
    - name: X-API-Version
      value: '1.0.0'
  params:
    - name: format
      value: json
      type: query
  auth:
    type: bearer
    token: '{{authToken}}'
  settings:
    timeout: 30000
    followRedirects: true
```
