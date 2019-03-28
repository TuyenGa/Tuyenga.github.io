---
layout: article
title: "Series học lập trình PHP MVC  Phần 4 Tạo cơ sở dữ liệu với mysql được tích hợp trong Xampp."
description: "Để thực hiện một chương trình thực tế chúng ta sẽ phải thành thạo sử dụng database. Ở đây hôm nay tôi sẽ tạo một database bằng mysql và một bảng với các dữ liệu ở trong đó. Và thực hiện kết nối php và mysql thông qua PDO. "
date: 2017-06-12  21:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích,PHP, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/12/Series-PHP-MVC-part-4-create-your-database-with-mysql-in-Xampp/
instant_title: "Series học lập trình PHP MVC  Phần 4 Tạo cơ sở dữ liệu với mysql được tích hợp trong Xampp."
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-06-preview.png
featured_image: /assets/media/featured-images/2017-06-06-featured.png
---

## Tạo database và bảng trong phpmyadmin của Xampp ##

phpmyadmin là một chương trình để thực hiện tạo database và bảng thông qua giao diện người dùng trực quan mà không sử dụng lệnh trực tiếp trên terminal.

Để vào phpmyadmin chúng ta phải bật apache và mysql trong xampp như hình sau:


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/XamppControl.PNG"
   alt="Bật Xampp Control"
   caption="Bật Xampp Control." %}

Và sau đó chúng ta sẽ vào [localhost/phpmyadmin][php] giao diện dù hơi cùi bắp nhưng nó mang lại cho ta hiệu quả và dễ sử dụng.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Giao-dien-cua-php-myadmin.PNG"
   alt="Giao diện Phpmyadmin"
   caption="Giao diện của phpmyadmin." %}

Đầu tiên chúng ta cick vào new để tạo database và điền tên vào. Tôi sẽ đặt tên cơ sở dữ liệu này là *mytodo* và đặt một bảng là *todos* có các trường cơ sở dữ liệu thứ tự như sau.

| Tên trường     | Kiểu dữ liệu    |
| :------------- | :------------- |
| id       | int       |
| description | varchar(100) |
| completed | boolean |


các bạn tạo bảng theo mẫu như vậy để chúng ta làm một mẫu todo list.

Tiếp theo chúng ta sẽ thực hiện kết nối cơ sở dữ liệu. Thông qua PHP và để chuẩn xác theo từng bước thì sẽ test thông qua index.

**Đầu tiên**

Chúng ta sẽ thực hiện kết nối bằng PDO bằng cách sử dụng cú pháp *new PDO ('mysql:host=localhost; dbname=Tên cơ sở dữ liệu (mytodo)','tên đăng nhập của phpmyadmin(default là root)', 'mật khẩu phpmyadmin (default là '')')*

và chúng ta sẽ thực hiện nó trong php như sau:

```php
<?php

try {
  $pdo = new PDO('mysql:host=localhost;dbname=mytodo','root','');

} catch (PDOException $e) {   
  die('Không thể kết nối'.$e->getMessage()); // khi ta không thể kết nối
}

$sql = 'select * from todos'; // lệnh chọn dữ liệu của sql

$statement = $pdo->prepare($sql);  // sử dụng $pdo để thực hiện lệnh sql

$statement->execute();  // đây là phương thức thực hiện lệnh trên

var_dump($statement->fetchAll()); // đưa ra kết quả bằng var_dump

 ?>

```

Nếu thành công thì kết quả trả về kết quả còn không thì nó sẽ trả lại lỗi cho chúng ta xem.
Và đây là hình ảnh của 2 kết quả.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Ket-Noi-Thanh-Cong.PNG"
   alt="Kết nối thành công"
   caption="Kết nối thành công." %}


{% include figure.html
  filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Khong-the-ket-noi.PNG"
      alt="Không Thể Kết nối"
      caption="Không thể kết nối và lỗi xuất hiện." %}

nếu thực hiện thành công được thì bạn đã hoàn thành bài này. Và chúng ta sẽ chuyển sang bài tiếp theo để thực hiện cấu trúc thư mục nhé. Chúc các bạn thành công.

[php]: https://localhost/phpmyadmin
