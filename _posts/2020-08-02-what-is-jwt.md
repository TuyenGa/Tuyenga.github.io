---
layout: post
title: "JSON Web Token là gì?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, authentication, Oauth, Oauth2.0]
image: assets/images/roadmap/authentication-jwt.png
---
JSON Web Token([JWT](https://tools.ietf.org/html/rfc7519)) là một phương tiện đại diện cho các yêu cầu chuyển giao giữa Client - Server. Các thông tin của chuỗi JWT được định  dạng bằng JSON trong đó chuỗi token phải có 3 phần là header, payload và signature. Ba phần này được ngăn bằng dấu "."

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/jwt.png" alt="Cấu trúc của JWT" /></p>

JWT bao gồm 3 phần Header, Payload và Signature các phần được phân biệt bởi dấu "."

## Cấu trúc của JSON Web Token

### Header

Phần **Header** sẽ chứa kiểu dữ liệu và thuật toán sử dụng để mã hoá chuỗi JWT.

```json
{
    "typ": "JWT",
    "alg": "HS256"
}
```

- "**typ**" (type): là kiểu dữ liệu chỉ ra rằng đối tượng là một JSON Web Token.
- "**alg**" (algothrim): là thuật toán ở đây **HS256** được xác định làm thuật toán mã hoá cho chuỗi.

### Payload

Phần **Payload** sẽ chứa các thông tin người dùng muốn mã hoá vào trong chuỗi **Token** vd **Email, username, userId ...** 

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/detail-jwt.png" alt="Chi tiết JWT" /></p>

Chi tiết từng thành phần trong chuỗi JWT sau khi được giải mã.

### Signature

Phần **Chữ ký** này là phần do người dùng tạo ra. Nó có thể là bất kỳ ký tự hoặc một đoạn văn bản nào đó được mã hoá để người khác khó có thể đoán hoặc giải mã được. Nó tương tự như password.

### Cuối cùng:

Kết hợp cả 3 thành phần lại và ngăn cách nhau bằng dấu "." thì ta được một kết quả như sau:

```json
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOlsidGVzdGp3dHJlc291cmNlaWQiXSwidXNlcl9uYW1lIjoiYWRtaW4iLCJzY29wZSI6WyJyZWFkIiwid3JpdGUiXSwiZXhwIjoxNTEzNzE.9nRhBWiRoryc8fV5xRpTmw9iyJ6EM7WTGTjvCM1e36Q
```

Chuỗi JWT này kết hợp với **Algorithm** cùng với **Signature** sẽ được giải mã ra phần **payload** cho người nhận hoặc server biết được nó có hợp lệ hay không.