# Script

**Definition**: Defines scripts executed during the request lifecycle

**Attributes**:

- `type` (string, Required): Execution moment. Options:
  - `before-request`: Executed before sending the request
  - `after-response`: Executed after receiving the response
  - `tests`: Executed for test validation
  - `hooks`: Executed for custom hooks
- `code` (string, Required): Executable code (JavaScript)

**Example**:

```yaml
scripts:
  - type: before-request
    code: |
      // Generate a timestamp for the request
      bru.setVar('timestamp', Date.now());
      console.log('Sending request...');
  - type: after-response
    code: |
      // Process response
      if (res.status === 200) {
        bru.setVar('token', res.body.token);
      }
```
