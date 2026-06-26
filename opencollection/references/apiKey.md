# API Key Authentication

**Definition**: API Key authentication

**Attributes**:

- `type` (string, Required): Must be `apikey`
- `key` (string, Optional): API key name
- `value` (string, Optional): API key value
- `placement` (enum: header | query, Optional): Where to place the API key

**Example**:

```yaml
type: apikey
key: X-API-Key
value: your-api-key-here
placement: header
```
