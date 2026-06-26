# Folder

**Definition**: A folder that groups related items within a collection

**Attributes**:

- `name` (string, Required): Name of the folder
- `type` (string, Required): Must be `folder`
- `children` (array, Required): List of child items in the folder
- `info` (ItemInfo, Optional): Metadata for the folder
- `docs` (string, Optional): Documentation for the folder

**Example**:

```yaml
- name: User Management
  type: folder
  info:
    description: All user-related operations
  children:
    - name: Get Users
      type: http
      http:
        method: GET
        url: '{{baseUrl}}/users'
    - name: Create User
      type: http
      http:
        method: POST
        url: '{{baseUrl}}/users'
  docs: |
    ## User Management
    This folder contains all operations related to user management including
    listing, creating, updating, and deleting users.
```
