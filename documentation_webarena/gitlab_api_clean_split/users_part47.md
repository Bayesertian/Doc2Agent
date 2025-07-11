## Unban user

DETAILS:
**Tier:** Free, Premium, Ultimate
**Offering:** Self-managed, GitLab Dedicated

> - [Introduced](https://gitlab.com/gitlab-org/gitlab/-/issues/327354) in GitLab 14.3.

Unbans the specified user. Available only for administrator.

```plaintext
POST /users/:id/unban
```

Parameters:

- `id` (required) - ID of specified user

Returns:

- `201 OK` on success.
- `404 User Not Found` if the user cannot be found.
- `403 Forbidden` when trying to unban a user that is not banned.

