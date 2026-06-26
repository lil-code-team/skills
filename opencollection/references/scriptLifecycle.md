# Scripts & Lifecycle

**Definition**: Scripts for collection execution lifecycle

**Attributes**:

- `type` (enum: before-request | after-response | tests | hooks, Required): The lifecycle stage when this script executes
- `code` (string, Required): The script code

**Script Types**:

- **before-request** - Executed before the request is sent. Use for setting up authentication, generating dynamic values, etc.
- **after-response** - Executed after receiving the response. Use for extracting values, setting variables, etc.
- **tests** - Run test assertions against the response
- **hooks** - Custom lifecycle hooks

**Execution Lifecycle**:

1. **Before-Request** - Executed before the request is sent
2. **Request Sent** - The actual HTTP request is made
3. **After-Response** - Executed after receiving the response
4. **Tests** - Run test assertions against the response

**Example**:

```yaml
- type: before-request
  code: |-
    // Set timestamp
    bru.setVar('timestamp', new Date().getTime());
- type: after-response
  code: |-
    // Extract auth token
    const token = res.body.token;
    bru.setVar('authToken', token);
- type: tests
  code: |-
    // Test response
    test('Status is 200', () => {
        expect(res.status).to.equal(200);
    });
- type: hooks
  code: // Custom lifecycle hooks
```
