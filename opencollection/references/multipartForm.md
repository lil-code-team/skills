# Multipart Form Body

**Definition**: Multipart form body

**Attributes**:

- `type` (string, Required): The body type identifier. Must be `multipart-form`
- `data` (array, Required): Form parts as array

**Data Item Structure**:

- `name` (string, Required): The form part name
- `type` (enum: text | file, Required): The type of form part
- `value` (string | array, Required): The form part value
- `description` (string, Optional): Description of the part
- `disabled` (boolean, Optional): Whether the form part is disabled

**Example**:

```yaml
type: multipart-form
data:
  - name: file
    type: file
    value: /path/to/file.pdf
    disabled: false
  - name: description
    type: text
    value: File description
    disabled: false
```
