# Raw Body

**Definition**: Raw request body with type and data

**Attributes**:

- `type` (enum: json | text | xml | sparql, Required): The type of raw body content
- `data` (string, Required): The raw body data

**Example**:

```yaml
type: json
data: |
  {
    "key": "value"
  }
```
