# Variables

**Definition**: A variable with name, value, description, and state flags

**Attributes**:

- `name` (string, Optional): The variable name
- `value` (VariableValue | array, Optional): The variable value
- `description` (string, Optional): Description of the variable
- `disabled` (boolean, Optional): Whether the variable is disabled

**Variable Types**:

Variables can have different value types and support variants for different contexts.

**Value Types**:

`string`, `number`, `boolean`,`null`, `object`

**Example**:

```yaml
name: apiEndpoint
value:
  - title: Production
    selected: true
    value:
      type: string
      data: https://api.example.com
  - title: Development
    selected: false
    value:
      type: string
      data: https://api.dev.example.com
description: API base endpoint URL
disabled: false
```
