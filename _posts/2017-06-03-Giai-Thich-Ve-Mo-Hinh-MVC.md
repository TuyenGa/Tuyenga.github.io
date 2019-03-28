---
layout: article
title: "Giải thích về mô hình MVC"
description: "Mô hình MVC Là viết tắt của Model-View-Controller, Đây là một mô hình kiến phần mềm được tạo ra với mục đích quản lý và xây dựng dự án phần mềm có hệ thống hơn ..."
date: 2017-06-03 12:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/03/Giai-thich-ve-mo-hinh-MVC/
instant_title: "Giải thích về mô hình MVC"
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-03-preview.png
featured_image: /assets/media/featured-images/2017-06-03-feature.png
---

Bước vào trong căn phòng của lập trình viên, bạn sẽ bị dội bom về các framework "Ruby on Rails", "Angular" hay "Laravel".

Nhìn chung, logic của mô hình MVC có thể được dùng để miêu tả qua quá trình làm web bằng các ngôn ngữ như PHP, Ruby,Python hay JavaScript.

Nhiều lập trình viên Web nhìn thế giới rộng lớn theo kiểu nhìn đời qua kẽ lá. Khi một lập trình viên khác nhìn vào code của họ, thì họ sẽ cho bạn một bài thuyết trình dài kèm theo những lý thuyết giáo điều quen thuộc.



{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-03-Minh-Hoa.png"
   alt="Mô Hình MVC"
   caption="Nhìn đời qua kẽ lá." %}
# Mô hình MVC là gì? #

**M là Model**: cấu trúc dữ liệu theo cách tin cậy và chuẩn bị dữ liệu theo lệnh của Controller.

**V là View**: Hiển thị dữ liệu cho người dùng theo cách dễ hiểu dựa trên hành động của người dùng.

**C là Controller**: Nhận lệnh từ người dùng, gửi lệnh đến Model để cập nhật dữ liệu, Truyền lệnh đến View để cập nhật giao diện hiển thị.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-03-MVC.png"
   alt="Mô Hình MVC"
   caption="Cơ chế hoạt động của mô hình MVC." %}

# Luồng xử lý trong mô hình MVC #

1. Người dùng gọi yêu cầu xử lý tại trang chủ.

2. "Controller" Nhận yêu cầu này và đưa lệnh xử lý yêu cầu đó.
Các lệnh thực thi với phần "View" thì cập nhật hoặc phục vụ yêu cầu trang web, với "Model" thì để trình diễn logic. Ta giả sử lệnh yêu cầu có yếu tố logic.

3. "Model" thực thi phần logic được lấy ra từ cơ sở dữ liệu và gửi trả lại phản hồi dựa trên hướng dẫn của "Controller".

4. "Controller" truyền dữ liệu ra phần "View", cập nhật giao diện hiển thị cho người dùng.

Với bất kì yêu cầu nào  đều phải đi qua **"Controller" trước khi chuyển hóa thành lệnh cho thực thi cho "View" hoặc "Model"."**

Nếu đã học framework lập trình web thì chắc chắn bạn sẽ phải gặp mô hình MVC

Nói ngắn gọn *Một khi bạn đã lập trình dựa trên mô hình MVC thì không phải ngán bất kỳ một framework nào cả.*

Nguồn: [freecodecamp][nguon] hãy đến đây để có thể hiểu thêm về bài viết.

[nguon]: https://medium.freecodecamp.com/model-view-controller-mvc-explained-through-ordering-drinks-at-the-bar-efcba6255053
