# WebSocket Request

**Definition**: WebSocket request configuration

**Attributes**:

- `info` (WebSocketRequestInfo, Optional): Metadata and documentation for the request
- `websocket` (WebSocketRequestDetails, Optional): WebSocket protocol details
- `runtime` (WebSocketRequestRuntime, Optional): Runtime configuration including variables, scripts, and assertions
- `docs` (string, Optional): Documentation for this request

**Example**:

```yaml
info:
  name: Real-time Updates
  type: websocket

websocket:
  url: 'ws://{{baseUrl}}/ws'
  protocols:
    - graphql-ws
  events:
    - type: message
      content: |
        { "type": "subscribe", "query": "subscription { newMessage { id content } }" }

runtime:
  variables:
    - name: subscriptionId
      value: '123'
  scripts:
    - type: on-connect
      code: |
        console.log('WebSocket connected');
  assertions:
    - expression: res.data
      operator: exists
      value: true
```

# WebSocket Request Info

**Definition**: WebSocket request metadata and documentation

**Attributes**:

- `name` (string, Optional): The name of the request
- `description` (string, Optional): Description of what the request does
- `type` (string, Optional): The type of request
- `seq` (Sequence, Optional): Sequence number for ordering
- `tags` (array, Optional): Array of tags for categorizing the request

**Example**:

```yaml
info:
  name: Real-time Updates
  description: Establishes WebSocket connection for real-time data
  type: websocket
  seq: 1
  tags:
    - websocket
    - realtime
```

# WebSocket Request Details

**Definition**: WebSocket request protocol details

**Attributes**:

- `url` (string, Optional): WebSocket endpoint URL
- `protocols` (array, Optional): Array of WebSocket subprotocols
- `events` (array, Optional): Array of WebSocket events to handle
- `body` (any, Optional): Initial message to send on connection

**Example**:

```yaml
websocket:
  url: 'ws://{{baseUrl}}/ws'
  protocols:
    - graphql-ws
    - json-protocol
  events:
    - type: message
      content: |
        { 
          "type": "subscribe", 
          "query": "subscription { newMessage { id content } }" 
        }
    - type: message
      content: |
        { "type": "ping" }
  body:
    type: json
    content:
      type: init
      payload: {}
```

# WebSocket Request Runtime

**Definition**: WebSocket request runtime configuration for variables, scripts, and assertions

**Attributes**:

- `variables` (array, Optional): Array of runtime variables
- `scripts` (Scripts, Optional): Scripts to execute at different lifecycle stages
- `assertions` (array, Optional): Array of assertions for response validation

**Example**:

```yaml
runtime:
  variables:
    - name: subscriptionId
      value: '123'
  scripts:
    - type: on-connect
      code: |
        console.log('WebSocket connected');
        bru.send('{ "type": "subscribe" }');
    - type: on-message
      code: |
        const data = JSON.parse(message);
        if (data.type === 'subscription') {
          bru.setVar('subscriptionId', data.id);
        }
  assertions:
    - expression: res.data
      operator: exists
      value: true
```
