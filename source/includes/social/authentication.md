# Social API

## 1. Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: abcdef0123abcdef0123"
```

> Make sure to replace `abcdef0123abcdef0123` with your API key.

GetSocial expects that an API key is included in all server requests, in a header as follows:

`Authorization: abcdef0123abcdef0123`

<aside class="notice">
You must replace <code>abcdef0123abcdef0123</code> with your personal API key.
</aside>