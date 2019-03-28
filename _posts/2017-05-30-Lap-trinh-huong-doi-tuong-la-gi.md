---
layout: article
title: "Lập trình hướng đối tượng là gì ?"
description: "Lập trình hướng đối tượng là một mẫu lập trình dựa trên khái niệm Công nghệ đối tượng, mà trong đó các đối tượng chứa đựng các dữ liệu, trên các trường, thường được gọi là thuộc tính và mã nguồn được tổ chức thành các phương thức."
date: 2017-05-30 12:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web]
comments: true
redirect_from:
  - /tutorials/2017/05/30/Lap-trinh-huong-doi-tuong-la-gi/
instant_title: "Lập trình hướng đối tượng là gì ?"
instant_kicker: Thế giới IT
preview_image: /assets/media/featured-images/2017-05-30-preview.png
featured_image: /assets/media/featured-images/2017-05-30-feature.png
---

Nội dung của bài viết bao gồm :

- Đối tượng là gì?
- Lập trình hướng đối tượng là gì?

## 1 - Đối tượng là gì? ##

Các đối tượng là điểm cốt lõi để hiểu về công nghệ hướng đối tượng. Bây giờ hãy nhìn xung quanh bạn sẽ nhìn thấy rất nhiều ví dụ về đối tượng ở thế giới thực : Con chó, cái bàn, tivi, xe đạp ...

Lập trình hướng đối tượng là một mẫu lập trình dựa trên khái niệm "công nghệ đối tượng" ...
Đối tượng trong thế giới thực đều có 2 đặc điểm. Tất cả đều có trạng thái và hành vi. Chó có trạng thái *( tên , màu sắc, loại, tình trạng đói hay no)*

Về mặt khái niệm thì các đối tượng phần mềm cũng như các đối tượng trong đời thực: Nó bao gồm các trạng thái và hành vi liên quan. Một đối tượng lưu trữ trạng thái của nó trong các trường (biến trong các ngôn ngữ lập trình) và thể hiện hành vi của mình thông qua các phương thức. Các phương thức thao tác trên các trạng thái bên trong của một đối tượng và được dùng như một cơ chế chính cho sự giao tiếp giữa các đối tượng với đối tượng. Việc ẩn đi các trạng thái bên trong và buộc các đối tượng đều phải được thực hiện thông qua các phương thức của một đối tượng được biết đến như là sự bao gói dữ liệu( data encapsulation) một nguyên lý cơ bản của lập trình hướng đối tượng.

## 2 - Lập trình hướng đối tượng là gì? ##

Lập trình hướng đối tượng *Object Oriented Programing(OOP)* được phát triển từ năm 2000 thay thế cho cách lập trình hàm thủ tục như trên [C][Cprogram]. Giúp người lập trình dễ dàng quản lý phát triển và quản lý code dễ dàng hơn.


Phương pháp lập trình này giải quyết các bài toán từ nhỏ đến lớn bằng cách quan sát và tưởng tượng những hành động, đặc điểm của thực thể thật ngoài đời sống và đem vào lập trình như một đối tượng ảo. Thể hiện qua các lớp(class), đối tượng(object), hành động(method) và đặc điểm chính là các biến(variable).

Nói cách khác:
- **OOP là nghệ thuật quan sát các đối tượng trong tự nhiên rồi cố gắng nắm bắt những hành động cùng đặc tính của chúng và biểu diễn dưới dạng đối tượng ảo trong ngôn ngữ lập trình.**

Lập trình hướng đối tượng luôn đi cùng 4 đặc điểm chính đó là:

- Encapsulation : Tính đóng gói.
- Inheritance : Tính kế thừa.
- Polymorphism : Tính đa hình.
- Abstraction : Tính trừu tượng.

**Các thuộc tính của lập trình hướng đối tượng.**

### Tính đóng gói(Encapsulation) và che giấu thông tin(Information hiding) ###

Trước khi tìm hiểu về tính đóng gói và che giấu thông tin. Các bạn nên tìm hiểu [cú pháp ngôn ngữ][Cuphap] các thể hiện tính chất public, private, protected ...

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-05-30-Encapsulation.png"
   alt="Encapsulation and Information hiding"
   caption="Tính đóng gói và che giấu thông tin" %}

Hình ảnh trên là một ví dụ về việc đóng gói và che giấu thông tin của phương thức OOP.
- Như bạn thấy viên thuốc được bao quanh chính là lớp vỏ Class.
- Method và variable là những thành phần bên trong thuốc được bao lại, che giấu đi và không thể nhìn thấy hoặc sử dụng nếu class bên trong không cho phép.

Và đó là tính đóng gói và che giấu thông tin của hướng đối tượng.

### Tính kế thừa (Inheritance) ###

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-05-30-InheritanceAndPolymorphysm.png"
   alt="Inheritance in OOP"
   caption="Kế thừa trong lập trình hướng đối tượng." %}

Trong thực tế, kế thừa là thừa hưởng lại nhữn gì mà người khác để lại.

Ví dụ: Con cái kế thừa của cha ...

Trong lập trình cũng vậy, kế thừa trong lập trình là cách một lớp có thể thừa hưởng lại những thuộc tính, phương thức từ một lớp đối tượng khác và sử dụng chúng như là của bản thân mình.

Một định nghĩa trừu tượng hơn về kế thừa: Là một đặc điểm của ngôn ngữ hướng đối tượng dùng để biểu diễn mối quan hệ **đặc biệt hóa - tổng quát hóa** giữa các lớp.

Ưu điểm của kế thừa:

* Cho phép xây dựng 1 lớp mới từ lớp đã có.

-- Lớp mới gọi là lớp con (subClass) hay lớp dẫn xuất(derived Class).

-- Lớp đã có gọi là lớp cha (supper Class) hay lớp cơ sở(base Class).

* Cho phép chia sẻ thông tin chung nhằm tái sử dụng đồng thời giúp ta dễ dàng  nâng cấp và bảo trì.

+ Định nghĩa sự tương thích giữa các lớp, nhờ đó ta có thể chuyển kiểu tự động.

### Tính đa hình (Polymorphism) ###

Tính đa hình Polymorphism : Poly(nhiều) + morphism(body) = nhiều hình thái khác nhau.

Tính đa hình được thể hiện qua việc viết lại các method từ Class cha thông qua Class kế thừa nó hoặc triển khai interface.

Và sau đây là một ví dụ.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-05-30-Polymorphysm.png"
   alt="Polymorphism in OOP"
   caption="Tính đa hình trong lập trình hướng đối tượng." %}

Các subClass là Class person, Class dogs, Class Cat, Class duck đều kế thừa method sua của supper Class Animal và override chúng để cách thể hiện ở mỗi Class là khác nhau.

### Tính trừu tượng, Phương thức ảo (Abstraction) ###

Nói một cách đơn giản thì bạn chỉ cần khai báo hàm trong lớp cha(access modifier, phương thức trả về, tên hàm, tham số truyền vào). Còn định nghĩa trong phần thân hàm bạn không cần quan tâm đến. Vì nó sẽ được khai báo lại từ class kế thừa.

**Định Nghĩa:** Đây là khả năng của bỏ qua hay không chú ý đến một khía cạnh của thông tin mà nó đang trực tiếp làm việc lên, nghĩa là nó có khả năng tập trung vào những cốt lõi cần thiết **(chỉ khai báo)**. Mỗi đối tượng phục vụ như là một "động tử" có thể hoàn thành công việc một cách nội bộ, báo cáo, thay đổi trạng thái của nó và liên lạc với các đối tượng khác mà không cần cho biết làm cách nào đối tượng tiến hành được các thao tác **(Sự override từ lớp con).** Tính chất này thường được gọi là sự trừu tượng dữ liệu.

* Phương thức ảo là phương thức được định nghĩa ở lớp cơ sở (lớp cha) mà các lớp dẫn xuất (lớp con) muốn sử dụng thì phải định nghĩa lại. Dùng từ khóa virtual(c++) hay abstract (java) để khai báo phương thức ảo:

--  Trong class ảo (abstract class) có thể có phương thức ảo(abstract method) hoặc không nhưng phương thức ảo bắt buộc phải ở trong class ảo.

--  Phương thức ảo không chứa body.

--  Khi kế thừa class ảo bắt buộc phải khai báo lại phương thức ảo của nó.

Và đó là 4 đặc điểm chính của hướng đối tượng. Mong rằng nó sẽ giúp các bạn phần nào đó trong học tập.







[Cprogram]: https://vi.wikipedia.org/wiki/C_(ng%C3%B4n_ng%E1%BB%AF_l%E1%BA%ADp_tr%C3%ACnh)

[Cuphap]: https://vi.wikipedia.org/wiki/C%C3%BA_ph%C3%A1p_ng%C3%B4n_ng%E1%BB%AF_C%2B%2B
