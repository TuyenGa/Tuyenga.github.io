---
layout: post
title: "Basic authentication"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, authentication, basic]
image: assets/images/roadmap/basicAuth.png
---

**Basic authentication** is a simple authentication scheme built into the HTTP Protocol. The client sends HTTP requests with the `Authorization` header that contains the word `Basic` word followed by a space and a base64-encoded string `username:password`. For example, to authorize as `demo /p@55w0rd` the client would send.

```javascript
Authorization: Basic ZGVtbzpwQDU1dzByZA==
```

**Note:** Because base64 is easily decoded, Basic authentication should only be used together with other security mechanisms such as HTTPS/SSL.

## Describing Basic Authentication

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/basic-authentication.png" alt="Basic Authentication" /></p>