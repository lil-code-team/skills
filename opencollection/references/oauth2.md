# OAuth 2.0 Authentication

**Description**: OAuth 2.0 supports multiple authorization flows. Choose the appropriate flow based on your application type.

# Client Credentials Flow

**Definition**: OAuth 2.0 Client Credentials flow

**Description**: Best for server-to-server authentication where no user interaction is needed.

**Attributes**:

- `type` (string, Required): Must be `oauth2`
- `flow` (string, Required): Must be `client_credentials`
- `accessTokenUrl` (string, Optional): URL to fetch the access token
- `refreshTokenUrl` (string, Optional): URL to refresh the token
- `credentials` (OAuth2ClientCredentials, Optional): Client credentials
- `scope` (string, Optional): Space-delimited OAuth 2.0 scopes
- `additionalParameters` (object, Optional): Additional parameters
- `tokenConfig` (OAuth2TokenConfig, Optional): Token configuration
- `settings` (OAuth2Settings, Optional): OAuth2 settings

**Example**:

```yaml
type: oauth2
flow: client_credentials
accessTokenUrl: 'https://api.example.com/oauth/token'
refreshTokenUrl: 'https://api.example.com/oauth/refresh'
credentials:
  clientId: 'your-client-id'
  clientSecret: 'your-client-secret'
  placement: body
scope: 'read write'
tokenConfig:
  id: 'myToken'
  placement:
    header: 'Authorization'
settings:
  autoFetchToken: true
  autoRefreshToken: true
```

## Resource Owner Password Flow

**Definition**: OAuth 2.0 Resource Owner Password Credentials flow

**Description**: Best for highly trusted applications where the user provides credentials directly to the app.

**Attributes**:

- `type` (string, Required): Must be `oauth2`
- `flow` (string, Required): Must be `resource_owner_password_credentials`
- `accessTokenUrl` (string, Optional): URL to fetch the access token
- `refreshTokenUrl` (string, Optional): URL to refresh the token
- `credentials` (OAuth2ClientCredentials, Optional): Client credentials
- `resourceOwner` (OAuth2ResourceOwner, Optional): Resource owner credentials
- `scope` (string, Optional): Space-delimited OAuth 2.0 scopes
- `additionalParameters` (object, Optional): Additional parameters
- `tokenConfig` (OAuth2TokenConfig, Optional): Token configuration
- `settings` (OAuth2Settings, Optional): OAuth2 settings

**Example**:

```yaml
type: oauth2
flow: resource_owner_password_credentials
accessTokenUrl: 'https://api.example.com/oauth/token'
credentials:
  clientId: 'your-client-id'
  clientSecret: 'your-client-secret'
  placement: body
resourceOwner:
  username: 'user@example.com'
  password: 'userpassword'
scope: 'read write'
```

## Authorization Code Flow

**Definition**: OAuth 2.0 Authorization Code flow

**Description**: Best for web applications with a backend server. Most secure and commonly used flow.

**Attributes**:

- `type` (string, Required): Must be `oauth2`
- `flow` (string, Required): Must be `authorization_code`
- `authorizationUrl` (string, Optional): URL to authorize the user
- `accessTokenUrl` (string, Optional): URL to fetch the access token
- `refreshTokenUrl` (string, Optional): URL to refresh the token
- `callbackUrl` (string, Optional): URL to callback to after authorization
- `credentials` (OAuth2ClientCredentials, Optional): Client credentials
- `scope` (string, Optional): Space-delimited OAuth 2.0 scopes
- `state` (string, Optional): Opaque value used for CSRF protection
- `pkce` (OAuth2PKCE, Optional): PKCE configuration
- `additionalParameters` (object, Optional): Additional parameters
- `tokenConfig` (OAuth2TokenConfig, Optional): Token configuration
- `settings` (OAuth2Settings, Optional): OAuth2 settings

**Example**:

```yaml
type: oauth2
flow: authorization_code
authorizationUrl: 'https://api.example.com/oauth/authorize'
accessTokenUrl: 'https://api.example.com/oauth/token'
callbackUrl: 'https://myapp.com/callback'
credentials:
  clientId: 'your-client-id'
  clientSecret: 'your-client-secret'
  placement: body
scope: 'read write'
state: 'random-state-string'
pkce:
  enabled: true
  method: S256
```

## Implicit Flow

**Definition**: OAuth 2.0 Implicit flow

**Description**: Best for single-page applications (SPAs). Note: This flow is deprecated in OAuth 2.1; consider using Authorization Code with PKCE instead.

**Attributes**:

- `type` (string, Required): Must be `oauth2`
- `flow` (string, Required): Must be `implicit`
- `authorizationUrl` (string, Optional): URL to authorize the user
- `callbackUrl` (string, Optional): URL to callback to after authorization
- `credentials` (object, Optional): Client credentials (implicit flow only needs clientId)
- `scope` (string, Optional): Space-delimited OAuth 2.0 scopes
- `state` (string, Optional): Opaque value used for CSRF protection
- `additionalParameters` (object, Optional): Additional parameters
- `tokenConfig` (OAuth2TokenConfig, Optional): Token configuration
- `settings` (OAuth2Settings, Optional): OAuth2 settings

**Example**:

```yaml
type: oauth2
flow: implicit
authorizationUrl: 'https://api.example.com/oauth/authorize'
callbackUrl: 'https://myapp.com/callback'
credentials:
  clientId: 'your-client-id'
scope: 'read write'
state: 'random-state-string'
```
