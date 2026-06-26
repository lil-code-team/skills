---
name: opencollection
description: Expert assistant for creating, reading, validating, transforming and executing OpenCollection API collections following the OpenCollection specification v1.0.0.
---

# OpenCollection Skill

You are an expert assistant for the **OpenCollection** specification.

OpenCollection is an open format for describing API collections, including requests, authentication, variables, environments, scripts and tests. Your purpose is to help users create, understand, validate and manipulate OpenCollection documents (`.json` or `.yaml`).

## Collection

**Definition**: The root object of an OpenCollection specification. This contains all the information about the API collection.

**Attributes**:

- `opencollection` (string, Optional): The version of the opencollection
- `info` (Info, Optional)
- `config` (CollectionConfig, Optional)
- `items` (array, Optional): Array of items in the collection
- `request` (RequestDefaults, Optional)
- `docs` (Documentation, Optional)
- `bundled` (boolean, Optional): True if the opencollection is a standalone file, false if stored on the filesystem with nested structure of folders and files
- `extensions` (Extensions, Optional)

**Example**:

```yaml
opencollection: '1.0.0'

info:
  name: My API Collection
  summary: A collection of API requests
  version: '1.0.0'

config:
  environments: []

items: []

request: {}

docs: Documentation for this collection
```

## References

- **Schema** [v1.0.0.json](references/v1.0.0.json)

- [Request Defaults](references/requestDefault.md)
- [Environment](references/environment.md)
- [Variables](references/variable.md)
- [Assertions](references/assertion.md)
- [Scripts & Lifecycle](references/scriptLifecycle.md)

- **Items**:
  - [HttpRequest](references/httpRequest.md)
  - [GraphQLRequest](references/graphqlRequest.md)
  - [GRPCRequest](references/grpcRequest.md)
  - [WebSocketRequest](references/websocketRequest.md)
  - [Folder](references/folder.md)
  - [Script](references/script.md)
- **Authentication**:
  - [AWS V4](references/auth/awsV4.md)
  - [OAuth 2.0](references/auth/oauth2.md)
  - [Basic Auth](references/auth/basic.md)
  - [Bearer Token](references/auth/bearer.md)
  - [Digest Auth](references/auth/digest.md)
  - [API Key](references/auth/apiKey.md)
  - [NTLM](references/auth/ntlm.md)
  - [WSSE](references/auth/wsse.md)
- **Request Body**:
  - [Form URL Encoded](references/requestBody/formUrlEncoded.md)
  - [Multipart Form](references/requestBody/multipartForm.md)
  - [Raw](references/requestBody/raw.md)

---
