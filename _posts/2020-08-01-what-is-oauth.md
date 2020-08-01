---
layout: post
title: "OAuth là gì?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, authentication, Oauth, Oauth2.0]
image: assets/images/roadmap/oauth.png
---

[OAuth 2.0](https://tools.ietf.org/html/rfc6749) là một giao thức mà nó cho phép người dùng cung cấp quyền truy cập trang web hoặc ứng dụng của bên thứ 3 truy cập vào tài nguyên được bảo vệ của họ, mà không cần thiết phải  ra  thông tin truy  cập dài hạn hoặc tiết lộ danh tính của họ.

---

## Các khái niệm trong OAuth

1. **Resource Owner**: Là chủ sở hữu dữ liệu mà khách hàng muốn chia sẻ. 
2. **Resource Server**: là nơi chứa thông tin dữ liệu cần chia sẻ. 
3. **Client**: Là bên thứ 3 website, ứng dụng muốn sử dụng các tài nguyên được chia sẻ.
4. **Authorization Server**: Là đối tượng quyết định việc cấp quyền truy cập vào dữ liệu cho client.

## Luồng hoạt động của giao thức OAuth

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/oauth2-generic-flow.png" alt="OAuth 2.0 Authentication Framework" /></p>

1. Client yêu cầu quyền truy cập từ Resource Owner để truy cập vào các tài nguyên.
2. Nếu  Resource Owner cho phép quyền truy cập này, Ứng dụng sẽ nhận được **Authorization Giant.** Đây là một chứng chỉ đại diện cho uỷ quền của Resource Owner.
3. Ứng dụng yêu cầu **Assess Token** bằng cách xác thực với **Authorization Server** và cấp **Authorization Giant.**
4. Ứng dụng sau khi được xác thực thành công và cấp phép uỷ quyền hợp lệ. **Authorization Server** sẽ phát hành **Access Token** và gửi nó cho ứng dụng.
5. Ứng dụng sẽ yêu cầu được truy cập vào tài nguyên được bảo vệ bởi **Resource Server**, và xác thực bằng **Access Token** đã được lấy trước đó.
6. Nếu như **Access Token** hợp lệ, **Resource Server** sẽ đáp ứng yêu cầu của ứng dụng.

## Kết luận

Vậy đó là OAuth 2.0 và cách nó hoạt động. Qua đây các bạn đã hiểu thêm kiến thức về OAuth và có thể ứng dụng nó vào trong ứng dụng của mình sử dụng OAuth.