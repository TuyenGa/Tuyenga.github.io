---
layout: article
title: "Series học lập trình PHP MVC phần 2 Cài đặt Text Editor chuẩn bị cho dự án của bạn."
description: "Text editor là một phần không thể thiếu khi các bạn dùng hầu hết thời gian để có thể code nhanh và đúng hơn. Bài hôm nay sẽ hướng dẫn các bạn cài đặt Sublime Text và các package cần thiết khi lập trình."
date: 2017-06-07 12:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích,PHP, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/07/Series-PHP-MVC-part-2-install-some-text-editor-prepare-your-project/
instant_title: "Series học lập trình PHP MVC phần 2 Cài đặt Text Editor chuẩn bị cho dự án của bạn."
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-06-preview.png
featured_image: /assets/media/featured-images/2017-06-06-featured.png
---

## Text editor là một phần rất quan trọng trong lập trình ##

Hiện nay có rất nhiều Text editor, mỗi loại có các ưu, nhược điểm riêng. Hôm nay chúng ta sẽ thực hiện cài đặt **Sublime Text** một text editor nổi tiếng, dễ cài đặt và dễ sử dụng phù hợp cho mọi người.

### Sublime Text 3 ###
* Sublime text là một trong những trình biên tập code có sẵn và phổ biến nhất hiện nay. Nó được yêu mến bởi nhiều lập trình viên do tốc độ, đơn giản, và môi trường Plugin phong phú.

* Để giúp các bạn nhận được nhiều hỗ trợ của sublime text 3. Tôi quyết định sẽ chia sẻ một danh sách những Plugin mà tôi yêu thích. Để giúp các bạn đỡ mất công tìm kiếm cũng như để lưu lại sau này sẽ dùng.

* Những tính năng trong bài viết sẽ giúp các web Developer thao tác nhanh chóng hơn. Package Control

* Sublime Text là một IDE nhẹ nhàng và nhiều tính năng hay. Bạn có thể thêm những tính năng mới thông qua việc cài đặt các plugin  hay package. Những plugin được thêm vào sẽ mở rộng thêm tính năng cho Sublime Text.

* Để cài được các package các bạn cần phải cài đặt Package Control.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/sublimetext3.png"
   alt="Sublime Text 3"
   caption="Sublime Text 3." %}

Đầu tiên, muốn cài đặt sublime text 3 chúng ta phải download nó từ [đây][linkdown].
Tiếp đến chúng ta cài đặt vô cùng đơn giản. Các bạn có thể tự thực hiện.

Sau đây tôi muốn giới thiệu các package cần thiết và giúp ích rất nhiều khi chúng ta code.

### Package Sublime Text 3 ###

**1. Emmet**

Đầu tiên phải kể đến là Package Emmet. Đây là package cho phép chúng ta gõ tắt code HTML và CSS cách dùng là dùng các cú pháp gõ tắt mà emmet hỗ trợ rồi dùng phím tap để thực hiện.

```html


<!-- DEMO -->
ul>p{Thẻ p}+li*3
<!-- press tab -->
<!-- Result: -->
<ul>
    <p></p>
    <li></li>
    <li></li>
</ul>

```

Các bạn có thể xem các lệnh gõ tắt tại [đây][detailEmmet]


**2. Bracket HighLighter**

Đây là package giúp bạn nhìn ra các phần Mở/đóng của thẻ nằm ở chỗ nào.


{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/Bracker HighLighter.png"
   alt="Bracket HighLighter"
   caption="Chi tiết package Bracket HighLighter" %}

**3. Color HighLighter**

Package này giúp bạn code css hay hơn bằng cách hiển thị màu sắc của mã màu.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/ColorHighLighter.gif"
   alt="Color HighLighter"
   caption="Chi tiết package Color HighLighter" %}

**4. Color Picker**

Package này giúp cho ta lấy được mã màu mà không cần dùng đến photoshop, Để mở hộp thoại chúng ta nhấn tổ hợp phím Clrt + Shift + C (package này mà kết hợp với package color highlighter thì tuyệt vời.)

   {% include figure.html
      filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/ColorPicker.png"
      alt="Color Picker"
      caption="Chi tiết package Color Picker" %}

**5. Sidebar Enhancements**

Package này tạo ra các context menu với nhiều tiện ích tốt như open in browser...

{% include figure.html
         filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/SidebarEnhancements.png"
         alt="Sidebar Enhancements"
         caption="Chi tiết package Sidebar Enhancements" %}

**6. Git**

Package này giúp bạn có thể làm việc với GIT một cách đơn giản hơn bằng các câu lệnh sẵn có.


{% include figure.html
    filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/GIT.png"
    alt="GIT"
    caption="Chi tiết package GIT" %}

**7. Advanced New File**

Package này cho phép bạn lưu file một cách chuyên nghiệp hơn. Để sử dụng ấn tổ hợp phím Ctrl + Alt + N

{% include figure.html
  filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/AdvancedNewFile.png"
  alt="Advanced New File"
  caption="Chi tiết package Advanced New File" %}

**8.Code Intel**

Package giúp bạn dễ dàng tìm ra các function, class,... đang sử dụng được viết từ đâu..


{% include figure.html
filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/CodeIntel.gif"
alt="Code Intel"
caption="Chi tiết package Code Intel" %}

**9. Auto file name**

Package này giúp hiển thị tất cả các file trong thư mục để các bạn có thể nhúng file đơn giản hơn.



{% include figure.html
  filename="/assets/media/posts/LapTrinh/2017-06-07-Gioi-thieu-va-cai-dat-Sublimetext3/AutofileName.gif"
  alt="AutofileName"
  caption="Chi tiết package Auto file Name" %}

[linkdown]: https://www.sublimetext.com/3

[detailEmmet]: https://docs.emmet.io/cheat-sheet/
