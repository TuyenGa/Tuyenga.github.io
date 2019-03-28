---
layout: article
title: "Series học lập trình PHP MVC  Phần 3 Tìm hiểu về cấu trúc thư mục trong dự án MVC"
description: "Hôm nay chúng ta sẽ tìm hiểu về cấu trúc thư mục của một chương chương trình PHP MVC gồm những thứ nào và tìm hiểu về chúng."
date: 2017-06-10  21:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích,PHP, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/10/Series-PHP-MVC-part-3-research-about-tree-folder-in-project-MVC/
instant_title: "Series học lập trình PHP MVC  Phần 3 Tìm hiểu về cấu trúc thư mục trong dự án MVC"
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-06-preview.png
featured_image: /assets/media/featured-images/2017-06-06-featured.png
---

## Tại sao phải tìm hiểu về cấu trúc thư mục. ##

Cấu trúc thư mục của một kiến trúc phần mềm như MVC là rất quan trọng. Để hiểu được MVC hoạt động như thế nào không khó nhưng để áp dụng được nó vào trong một ngôn ngữ thường là rất khó. Giống nhiều người bạn của mình, hiểu rất tường tận về lý thuyết MVC nhưng do nắm không chắc ngôn ngữ nên dù có giải thích như thế nào đi nữa thì họ cũng khó lòng mà áp dụng được một kiến trúc phần mềm vào trong ngôn ngữ.

Và hôm nay chúng ta cùng tìm hiểu cấu trúc thư mục của MVC nhé.

## Cấu trúc thư mục MVC ##

Có rất nhiều kiến trúc phần mềm quan trọng mà chúng ta nên tìm hiểu như client Server, MVP, MVC, ... Hiểu nhiều kiến trúc khác nhau giúp các bạn nắm được lý thuyết về chúng và dễ áp dụng vào các bài toán khác nhau.

Hầu hết để nắm được một kiến trúc phần mềm chúng ta nên tìm hiểu cấu trúc thư mục của kiến trúc đó.

Và đây là cấu trúc thư mục chuẩn của mô hình MVC (Theo mình làm là như vậy :D).

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Cau-truc-thu-muc-MVC.PNG"
   alt="Cấu Trúc Thư Mục Mô Hình MVC"
   caption="Cấu Trúc Thư Mục Mô Hình MVC." %}

Theo như hình trên chúng ta cũng đã thấy được cơ bản về cấu trúc thư mục của mô hình MVC. Cấu trúc thư mục của mô hình MVC bao gồm 3 phần chính và các phần phụ.

Phần chính của thư mục là phần controllers, core, và views. Các phần phụ là public và các file index.php, config.php, và routes.php dùng để làm cho mô hình MVC thêm phần chặt chẽ hơn.

### controllers ###

controllers là tên của thư mục chứa các thành phần Controller dùng để kết nối core(Model) và phần views với nhau và điều khiển các.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Cau-Truc-controllers.PNG"
   alt="Cấu Trúc Thư Mục Controller"
   caption="Cấu Trúc Thư Mục controllers." %}

rất đơn giản phải không nào.

### core ###

core là tên thư mục chứa các thành phần Model dùng để kết nối cơ sở dữ liệu và thực hiện các lệnh trên database. Khi Controller có yêu cầu Model sẽ thực hiện kết nối tới cơ sở dữ liệu và thực hiện lệnh trong đó.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Cau-Truc-core.PNG"
   alt="Cấu Trúc Thư Mục Model"
   caption="Cấu Trúc Thư Mục core." %}

Ở đây thư mục database có nhiệm vụ kết nối với cơ sở dữ liệu và thực hiện các lệnh liên quan đến cơ sở dữ liệu.

File bootstrap.php là file liên quan trực tiếp đến thư mục index.php. Nó cho phép thư mục index.php Không cần phải khai báo nhiều file để gọi các hàm mà hầu hết sẽ thực hiện khai báo file liên quan đến index trong file bootstrap.php này.

File Request.php có nhiệm vụ là lấy Uri trên browser và gửi về routes.php

File Router.php là file thực hiện load file routes.php để Có thể Request trên Uri

### views ###

views là tên thư mục chứa các thành phần giao diện để hiển thị trực tiếp cho người dùng xử lý và gọi vào trong controller thông qua router.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/Cau-Truc-views.PNG"
   alt="Cấu Trúc Thư Mục views"
   caption="Cấu Trúc Thư Mục views." %}

view ở đây sẽ hiển thị hết thông tin người dùng và các chức năng của chương trình ra để người dùng có thể sử lý.

### public ###

Thư mục public có nhiệm vụ lưu trữ file css, js hoặc hình ảnh ở đó để cho view có thể hiển thị ra.

### index.php ###

file này để server load chương trình ra thông qua index.

### routes.php ###

Bao gồm các lệnh trên uri để có thể khai báo được controller vào trong index.php


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-12-Cau-Truc-Thu-Muc-MVC/routes.PNG"
   alt="thành phần trong routes"
   caption="Thành phần trong routes." %}

Như vậy chúng ta đã tìm hiểu hết thư mục của một mô hình MVC đơn giản. Vậy sau này chúng ta xây dựng một chương trình MVC hãy xây dựng theo mô hình này nhé. Chúc các bạn vui vẻ.
