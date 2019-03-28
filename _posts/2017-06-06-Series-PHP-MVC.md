---
layout: article
title: "Series học lập trình PHP MVC"
description: "PHP được xây dựng theo mô hình MVC sẽ giúp người sử dụng dễ dàng quản lý và bảo trì code hơn so với khi xây dựng kiểu thông thường. Hôm nay bài viết về PHP MVC sẽ nêu chi tiết cách làm mà trước đây mình cũng rất khó khăn để có thể tìm hiểu được. Hi vọng sẽ giúp được các bạn."
date: 2017-06-06  12:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích,PHP, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/06/Series-hoc-lap-trinh-PHP-MVC/
instant_title: "Series học lập trình PHP MVC"
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-06-preview.png
featured_image: /assets/media/featured-images/2017-06-06-featured.png
---

Đây là loạt Tutorials về PHP MVC mình làm dành cho các bạn mới học lập trình hoặc chưa nắm rõ kiến thức về lập trình php theo mô hình MVC. Đây cũng là để mình ôn lại những kiến thức mình đã học được.

Thầy mình có nói rằng: **Cách học tốt nhất là tự tìm hiểu và chia sẻ với người khác.** nên hôm nay mình sẽ chia sẻ với các bạn bài viết này.

Loạt bài này sẽ giúp các bạn có những kỹ năng, kiến thức sau:

1. Hiểu hơn về MVC và hướng đối tượng.

2. Cách code PHP thuần dựa trên mô hình MVC.

3. Cách cài đặt và sử dụng server Xampp và hệ quản trị cơ sở dữ liệu Mysql.

## Phần 1: Giới thiệu và cài đặt XAMPP ##

### Giới thiệu ###

Hiện tại mình thấy rất nhiều bạn có kiến thức rất tốt về MVC, OOP nhưng để áp dụng vào các ngôn ngữ thực tế thì chưa nắm chắc nên nay mình xin được giới thiệu về khóa học này dựa trên ngôn ngữ PHP để cho các bạn mới học hoặc các bạn đang bị rỗng kiến thức về MVC PHP.

Mình thấy có rất nhiều khóa học về MVC PHP nhưng không phải vì vậy mà mình không làm series về học lập trình MVC PHP này tại vì mình thấy các khóa học trên mạng hiện nay đều không hướng trọng tâm về cấu trúc thư mục của MVC và không giải thích được rõ nên dùng các đối tượng như thế nào. Nên series này sẽ làm rõ vấn đề đó. Và mục tiêu của khóa học này cũng là để nâng cao khả năng xử lý khi làm việc và học tập cũng như để mình ôn lại các kiến thức về [MVC][Mvc], [OOP][oop].

### Hướng dẫn cài đặt Xampp Server ###

Để thực hiện chạy chương trình MVC PHP chúng ta sẽ sử dụng cơ sở dữ liệu Mysql và server Apache. Để cài đặt được nhanh và thuận tiện thì mình sẽ dùng Xampp để thực hiện chương trình.

1- Để thực hiện cài đặt mình sẽ down xampp ở [đây][day].

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-06-GioiThieuVaCaiDatXampp/download.png"
   alt="download xampp"
   caption="Download Xampp cho Windows." %}

Vì mình sử dụng Windows để hướng dẫn nên mình sẽ hướng dẫn các bạn cài xampp trên windows. Đây là bản 32 bit nhưng các bạn 64 bit cứ tải về để cài đặt như bình thường.

2- Tiếp theo là đến phần cài đặt.

Các bạn cứ next và đến khi gặp phần Select Components . Nếu các bạn chỉ cài xampp để thực hiện series này thì chỉ cần chọn như hình sau. Còn để thực hiện các web khác thì các bạn có thể để hết.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-06-GioiThieuVaCaiDatXampp/SelectComponents.png"
   alt="Select Components"
   caption="Chọn các thành phần cho Xampp Server." %}

3- Tiếp theo chỉ cần đợi và ấn finish là đã hoàn thành phần cài đặt xampp.

Giờ chỉ cần chạy xampp lên và thực hiện chạy xampp và Mysql là các bạn có thể thực hiện được series này rồi.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-06-GioiThieuVaCaiDatXampp/StartXampp.png"
   alt="Start Xampp"
   caption="Ấn vào nút start của mysql và apache để thực hiện chạy xampp." %}

Và chạy [localhost][local]/ten-tap-tin để có thể chạy project.

vd: Thư mục chúng ta đặt vào htdocs tên là PHPMVC thì chúng ta sẽ chạy http://localhost/PHPMVC

Như vậy chúng ta đã thực hiện cài đặt xong Xampp vậy từ sau này trở đi chúng ta sẽ dùng xampp để thực hiện các bài trong series PHP MVC này.



[local]: http://localhost
[oop]: https://tuyenga.github.io/laptrinh/2017/05/30/Lap-trinh-huong-doi-tuong-la-gi
[Mvc]: https://tuyenga.github.io/laptrinh/2017/06/03/Giai-Thich-Ve-Mo-Hinh-MVC
[phan1]: https://tuyenga.github.io/LapTrinh/2017/06/06/Series-hoc-lap-trinh-PHP-MVC/
[day]: https://www.apachefriends.org/download.html
