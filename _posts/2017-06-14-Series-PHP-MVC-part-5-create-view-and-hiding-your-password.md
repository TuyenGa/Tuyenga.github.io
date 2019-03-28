---
layout: article
title: "Series học lập trình PHP MVC  Phần 5 Tạo giao diện người dùng và ẩn đi password cơ sở dữ liệu của bạn."
description: "Để chương trình được bảo mật về cơ sở dữ liệu và cấu trúc tốt hơn thì ta sẽ thực hiện các bước tiếp theo để có thể cấu trúc được cơ bản về MVC nhé."
date: 2017-06-14  15:00:00  +0700
categories: [LapTrinh]
tags: [blog, jekyll, github, web, MVC, Tutorials, Giải thích,PHP, Model, Controller, View]
comments: true
redirect_from:
  - /tutorials/2017/06/14/Series-PHP-MVC-part-5-create-view-and-hiding-your-password/
instant_title: "Series học lập trình PHP MVC  Phần 5 Tạo giao diện người dùng và ẩn đi password cơ sở dữ liệu của bạn."
instant_kicker: IT
preview_image: /assets/media/featured-images/2017-06-06-preview.png
featured_image: /assets/media/featured-images/2017-06-06-featured.png
---

## Tạo giao diện người dùng. Giao diện Home Page. ##

Giao diện ở đây thực sự không quá quan trọng. Nó chỉ để chúng ta biết được chúng ta đang ở đâu nên tôi sẽ tạo một giao diện đơn giản. Show data của cơ sở dữ liệu ra ngoài màn hình.


Để tạo một giao diện chúng ta sẽ tạo một file là **index.view.php** . File này có nhiệm vụ show Htlm vs Css của chương trình web của chúng ta. Thực hiện như sau.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home Page</title>
  </head>
  <body>
    <h1>Home Page</h1>
    <ul>
      <?php foreach ($tasks as $task): ?>
        <li>
            <?php if ($task->completed): ?>
              <strike><?=$task->description ?></strike>
              <?php else: ?>
                <?=$task->description ?>
            <?php endif; ?>
        </li>
      <?php endforeach; ?>
    </ul>
  </body>
</html>
```

Theo chương trình này thì chúng ta sẽ có một mảng $tasks và chúng ta sẽ dùng foreach gán nó vào cho từng phần tử là $task để thực hiện lấy ra các dữ liệu.

Hôm trước chúng ta đã [tạo cơ sở dữ liệu][database] có một trường là completed và kiểu dữ liệu là boolean nên hôm nay chúng ta dùng if để kiểm tra xem nếu nó false thì chúng ta sẽ gạch bỏ nó đi còn nếu nó true thì sẽ in nó ra.

{% include figure.html
   filename="/assets/media/posts/LapTrinh/2017-06-14-Tao-giao-dien-nguoi-dung-va-an-password/ket-qua-view.PNG"
   alt="Kết quả view"
   caption="Kết quả sau khi thực hiện thành công." %}


## Tiếp theo chúng ta sẽ cấu trúc thư mục MVC theo hướng có một chút bảo mật. ##

Chúng ta sẽ tạo một thư mục **core** và trong đó có một thư mục là **models** và tạo thêm một file là *Connection.php* để có thể thực hiện được connect.

Hôm trước chúng ta kết nối cơ sở dữ liệu trên file *index.php* nhưng để tăng tính bảo mật chúng ta sẽ kết nối thông qua file *Connection.php*. Trước khi tạo file đó chúng ta tạo file *config.php* trước để thực hiện tạo config.

```php

<?php

return [
  'database' =>[

    'name' => 'mytodo',  // Tên cơ sở dữ liệu
    'username' => 'root',  // Tên đăng nhập phpmyadmin
    'password' => '',     // mật khẩu đăng nhập phpmyadmin
    'connections' => 'mysql:host=127.0.0.1', // tên database và host mặc định
    'options' => [      // cài đặt thêm để hiển thị lỗi  hoặc kiểu dữ liệu.
      PDO::ATTR_ERRMODE => PDO::ERRMODE_WARNING
    ]
  ]

];

 ?>

```

Như vậy chúng ta đã thực hiện config xong. bây h các bạn thay tên cơ sở dữ liệu và có thể tiếp tục bài học.

Tiếp theo chúng ta sẽ làm về file *Connection.php*.

```php
<?php

class Connection
{

  public static function make($config)
  {
    try {
      return new PDO(
          $config['connections'].';dbname='.$config['name'],
          $config['username'],
          $config['password'],
          $config['options']

      );
    } catch (PDOException $e) {
      die('Không thể kết nối. '.$e->getMessage());
    }

  }

}

 ?>

```

Như vậy là đã hoàn thành kết nối với cơ sở dữ liệu và ẩn được các dữ liệu bí mật của bạn. Ở đây ta dùng hàm static để có thể tạo kết nối một cách nhanh chóng mà không cần quá nhiều lần khai báo biến.

Tiếp theo chúng ta sẽ tạo 1 file *QueryBuilder.php* ở trong **models** để có thể lấy dữ liệu từ trong database ra ngoài. Thông qua kết nối cơ sở dữ liệu trong file *Connection.php* như sau.

```php

<?php

class QueryBuilder
{

  protected $pdo;   // khởi tạo một biến pdo để có thể tương tác với các hàm trong class

  public function __construct($pdo)   
  // tạo một constructor để có thể lấy biến pdo ở bên lớp Connection
  {
    $$this->pdo = $pdo;
  }

  public function selectAll($table) // tạo một phương thức với tên của table để lấy dữ liệu.
  {
    $sql = "Select * from {$table}";

    $statment = $$this->pdo->prepare($sql);

    $statment->execute();

    return $statement->fetchAll(PDO::FETCH_OBJ); // trả về kiểu dữ liệu.
  }

}


 ?>

```

Giờ chúng ta sẽ tạo một file *bootstrap.php* để khai báo và thực hiện connect database trong đó và chỉ việc gọi nó ra *index.php* là có thể sử dụng được rồi.

**bootstrap.php**

```php
<?php
$app = []; // tạo ra một mảng có tên là app để có thể tùy biến khai báo config

$app['config'] = require 'config.php'; // khai báo config với tên app['config']

require 'core/models/Connection.php'; // khai báo Connection.php
require 'core.models/QueryBuilder.php'; // khai báo QueryBuilder.php

$app['database'] = new QueryBuilder(  
  /*
  đối tượng QueryBuilder có constructor $pdo và đối tượng static ở trong chính là Hàm static chúng ta đã tạo ra ở trong class Connection.
*/
  Connection::make($app['config']['database'])

);


```

Như vậy chúng ta đã nắm bắt được hầu hết cấu trúc MVC và cũng đã hầu như hoàn thành được phần kết nối và bảo mật của MVC . Các bạn download mã nguồn tại [đây][day]



[database]: https://tuyenga.github.io/laptrinh/2017/06/12/Series-PHP-MVC-part-4-create-your-database-with-mysql-in-Xampp

[day]: https://github.com/TuyenGa/PHP-practitioner.git
