---
layout: post
title: "HTTP là gì?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, protocol, HTTP, HTTPS]
image: assets/images/roadmap/HTTP.png
---

HTTP(HyperText Transfer Protocol) Là giao thức truyền tải siêu văn bản. Đây là một giao thức tiêu chuẩn cho World Wide Web(WWW) để truyền tải dữ liệu âm thanh, văn bản, hình ảnh, videos từ Web Server tới trình duyệt của người dùng.

### Sơ đồ hoạt động của HTTP.

HTTP hoạt động dựa trên mô hình Client - Server. Việc truy cập website được tiến hành dựa trên các giao tiếp của 2 đối tượng trên. Khi trình duyệt truy cập đến trang web thông qua HTTP nó sẽ thực hiện các phiên kết nối đến Server thông qua địa chỉ IP do hệ thống DNS cung cấp thực hiện phân giải từ tên miền mà trình duyệt cung cấp. Sau khi Server nhận lệnh nó sẽ trả về các mã lệnh tương ứng để hiển thị website, văn bản, hình ảnh hoặc âm thanh.

### Các thành phần chính của HTTP.

**HTTP-Requests**

**HTTP Request Method:** Là phương thức để chỉ ra hành động mong muốn được thực hiện trên tài nguyên đã xác định.

Cấu trúc một HTTP Request:

- Một Request-line = Phương thức + URI-request + phiên bản HTTP. Giao thức HTTP định nghĩa một trong các phương thức GET, POST, PUT, HEAD, DELETE ... Client có thể sử dụng một trong các phương thức đó để gửi Request lên cho Server.
- Có thể có hoặc không các trường Headers.
- Một dòng trống để đánh dấu sự kiện kết thúc của các trường Header.

Requesst Header Fields: Các trường header cho phép client truyền thông tin bổ xung về yêu cầu và về chính client đến server.

- Tuỳ chọn Dữ liệu gửi lên.

Khi Request đến server thì server sẽ thực hiện một trong 3 hành động sau:

- Phân tích Request nhận được và map yêu cầu với tập tin trong tài liệu sau đó trả lại kết quả cho chương trình.

- Nhận yêu cầu từ Request và ra lệnh cho một chương trình bên trong server để thực thi và trả lại kết quả.

- Request từ client không hợp lệ hoặc có lỗi sẽ được thông báo lại cho phía người dùng.

**HTTP-Response**
Cấu trúc của một HTTP Response:
- Một Status-line = Phiên bản HTTP + Mã trạng thái + Trạng thái.
- Có thể có các trường Headers.
- Một dòng đánh dấu kết thúc sự kiện Header.
- Dữ liệu trả về.

Mã trạng thái: Thông báo kết quả khi nhận được yêu cầu xử lý cho bên client biết.

Các kiểu mã trạng thái:
- 1xx: Thông báo thông tin(100 -> 101)
- 2xx: Thông báo thành công(200 -> 206)
- 3xx: Thông báo sự điều hướng của URI (300 -> 307)
- 4xx: Thông báo lỗi của phía client (400 -> 417)
- 5xx: Thông báo lỗi phía Server(500 -> 505)

## Kết luận
Hiểu đơn giản HTTP là một giao thức được tạo ra để giao tiếp qua lại giữa Client và Server bằng các phương thức HTTP Request và HTTP Response.