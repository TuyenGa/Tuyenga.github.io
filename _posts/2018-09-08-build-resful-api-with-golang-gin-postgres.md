---
layout: article
title: "Xây dựng Resful APIs với framework Gin của Golang với Postgresql."
description: "Giống như bài xây dựng ứng dụng CURD đơn giản hôm nay chúng ta sẽ cùng tìm cách xây dựng một ứng dụng golang được kết nối với Postgresql CURD với Gin framework."
date: 2018-09-08 12:00:00  +0700
categories: [laptrinh]
tags: [blog, jekyll, github, talking, how, to, golang, gin, postgres]
comments: true
redirect_from:
  - /tutorials/2018/09/08/build-resful-api-with-golang-gin-postgres/
instant_title: "develop"
instant_kicker: software
---

# Xây dựng ứng dụng Golang.

Để xây dựng một ứng dụng golang chúng ta làm [tại đây](https://tuyenga.github.io/laptrinh/2018/09/03/make-new-golang-project)

Làm theo hướng dẫn để tạo ra được một file `main.go`, `go.mod` như vậy chúng ta đã sẵn sàng để đi đến bước tiếp theo.

# Tạo ra các thư mục cơ bản.

Cây thư mục của project.

{% include figure.html
  filename="/assets/media/posts/LapTrinh/2018-09-08-tree-folder.png"
  alt="Tree folder"
  caption="Cây thư mục của project" %}

Các bạn tạo ra một cây thư mục đơn giản như trên và chúng ta bắt đầu đi từng phần một.

## Thêm thư viện postgres cho dự án.

Trước khi xây dựng dự án chúng ta phải cài đặt gin framework, postgresql library.

- Cài gin framework.

Các bạn bật terminer của linux và macos hoặc cmd của window lên và đánh lệnh dưới đây.

`go get github.com/gin-gonic/gin`

Gin sẽ giúp chúng ta xử lý router và trả về dạng Json nhanh và gọn hơn. Các bạn có thể dùng các framework khác hoặc dùng thẳng thư viện `net/http` của golang.

- Cài postgres library cho golang.

Chúng ta chạy lệnh `go get github.com/lib/pq`

Thư viện này là bắt buộc phải sử dụng nếu chúng ta muốn kết nối với postgres nó cho phép ta thực thi kết quả trả về của thư viện `database/sql`.

## Xây dựng Ứng dụng Resful APIs.

1. Kết nối với database.

Đầu tiên chúng ta vào trong thư mục `models` và tạo ra file `model.go`

Trong file này chúng ta sẽ tạo ra các kết nối đến database postgres.

```golang
package models

import (
  "fmt"
  "database/sql"
  _ "github.com/lib/pq"
)
var db *sql.DB
const (
  //khai báo host của database. Thường sẽ là localhost
  DB_HOST = "localhost"
  //khai báo Port của database.
  DB_PORT = 5432
  //user name login vào database.
  DB_USER = "postgres"
  //password login vào database.
  DB_PASSWORD = "postgres"
  //tên của database.
  DB_DATABASE_NAME = "demo_golang"
  // ngoai cach khai bao nay các bạn có thể tham khảo thêm file .env
)

func GetPostgresDb() (*sql.DB, error) {
  host := DB_HOST
  port := DB_PORT
  user := DB_USER
  password := DB_PASSWORD
  dbname := DB_DATABASE_NAME

  desc := fmt.Sprintf("host=%s port=%d user=%s password=%s dbname=%s sslmode=disable", host, port, user, password, dbname)

  db, err := ConnectToProtgres(desc)
  if err != nil {
    return nil, err
  }
  return db, nil
}

func ConnectToPostgres(desc string) (*sql.DB, error) {
  db, err := sql.Open("postgres", desc)
  if err != nil {
    return nil, err
  }

  return db, nil
}
```

2. Tạo file kiểu dữ liệu cho data. Profile Struct.

Trong thư mục `models` chúng ta tạo thêm một file là `profile.go`.
File này có tác dụng định nghĩa kiểu dữ liệu cho data.

```golang
package models

type User struct { // kiểu dữ liệu User dùng để định nghĩa từng phần tử của từng user.
  ID int `json:"id"`
  Name string `json:"name"`
  Age int `json:"age"`
}

var People []User //kiểu People là một mảng gồm nhiều user khác nhau.
```

3. Khởi Tạo controllers.

Tạo ra một file controller.go trong thư mục controllers. File này có tác dụng xử lý và điều khiển luồng dữ liệu từ trong database sau khi được kết nối với database và trả về dưới dạng json.

```golang
package controllers

import (
  "gin-app/models" // khai báo models trong database để sử dụng các kiểu dữ liệu và kết nối data. gin-app là modules mà bạn cài đặt trong go.mod.
  "github.com/gin-gonic/gin"
  "net/http"
  "strconv"
)
// hàm dưới được dùng để lấy hết dữ liệu từ một bảng trong database ra và hiển thị chúng dưới dạng json.
func GetPeople(c *gin.Context) {
  query := `SELECT * from profile`

  db, err := models.GetPostgresDb()
  if err != nil {
    c.JSON(http.StatusInternalServerError, gin.H{"status": http.StatusInternalServerError})
  }
  var people models.People
  rows, err := db.Query(query)
  if err != nil {
    panic(err))
  }
  defer rows.Close()

  for rows.Next() {
    var user models.User

    err = rows.Scan(&user.ID, &user.Name, &user.Age)
    if err != nil {
      panic(err)
    }

    people = append(people, user)
  }

  c.JSON(http.StatusOK, gin.H{"status": http.StatusOK, "result": people})
}
```

Như vậy về cơ bản đã hoàn thành xong Connect database và tạo ra được controller cho project. [Xem tiếp phần sau]() để hoàn thành project nhé.