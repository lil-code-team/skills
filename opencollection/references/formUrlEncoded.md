# Form URL Encoded Body

**Definition**: Form URL encoded body

**Attributes**:

- `type` (string, Required): The body type identifier. Must be `form-urlencoded`
- `data` (array, Required): Form fields as array of key-value pairs

**Data Item Structure**:

- `name` (string, Required): The form field name
- `value` (string, Required): The form field value
- `description` (string, Optional): Description of the field
- `disabled` (boolean, Optional): Whether the form field is disabled

**Example**:

```yaml
type: form-urlencoded
data:
  - name: username
    value: john_doe
    disabled: false
  - name: password
    value: secret123
    disabled: false
```
