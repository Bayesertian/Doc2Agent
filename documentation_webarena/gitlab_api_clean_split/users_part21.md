## Single SSH key

Get a single key.

```plaintext
GET /user/keys/:key_id
```

Parameters:

| Attribute | Type   | Required | Description          |
|-----------|--------|----------|----------------------|
| `key_id`  | string | yes      | ID of an SSH key |

```json
{
  "id": 1,
  "title": "Public key",
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAIEAiPWx6WM4lhHNedGfBpPJNPpZ7yKu+dnn1SJejgt4596k6YjzGGphH2TUxwKzxcKDKKezwkpfnxPkSMkuEspGRt/aZZ9wa++Oi7Qkr8prgHc4soW6NUlfDzpvZK2H5E7eQaSeP3SAwGmQKUFHCddNaP0L+hM7zhFNzjFvpaMgJw0=",
  "created_at": "2014-08-01T14:47:39.080Z"
}
```

