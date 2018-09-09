---
layout: article
title: "Xây dựng Resful APIs với framework Gin của Golang với Postgresql Phần 2."
description: "Tiếp theo của Xây dựng Resful APIs với Gin và postgres chúng ta sẽ tiếp tục tìm hiểu và hoàn thiện hệ thống resful APIs của chúng ta."
date: 2018-09-09 12:00:00  +0700
categories: [laptrinh]
tags: [blog, jekyll, github, talking, how, to, golang, gin, postgres]
comments: true
redirect_from:
  - /tutorials/2018/09/08/build-resful-api-with-golang-gin-postgres-part-2/
instant_title: "develop"
instant_kicker: software
---

Tiếp theo của Xây dựng Resful APIs với Gin và postgres chúng ta sẽ tiếp tục tìm hiểu và hoàn thiện hệ thống resful APIs của chúng ta.

## Xây dựng controllers.

Tiếp tục hoàn thiện file `controller.go` của chúng ta.

```golang
// hàm naỳ được viết tiếp vào file controller mà chúng ta đã xây dựng từ bài trước.
func Create(c *gin.Context) {
  // Trước khi tạo ra một bản ghi cho database
  // chúng ta sẽ tạo ra định dạng dữ liệu truyền vào trước.
  // kiêủ dữ liệu User trong file models/profile.go
  user := new(models.User)
  // tạo query cho hàm create
  query := `INSERT INTO profile (name, age) VALUES ($1, $2) returning *`
  // connect vào database
  db, err := models.GetProgresDb()
  if err != nil {
    panic(err))
  }

  statement, err := db.Prepare(query)
  if err != nil {
    panic(err))
  }
  defer statement.Close()

  name := c.PostForm("name")
  age, _ := strconv.Atoi(c.PostForm("age")) // convert string sang int

  err = statement.QueryRow(name, age).Scan(&user.ID, &user.Name, &user.Age)

  if err != nil {
    panic(err))
  }

  c.JSON(http.StatusCreated, gin.H{"status": http.StatusCreated, "result": user})
}
// hàm update cho database
func Update(c *gin.Context) {
  user := new(models.User)
  query := `UPDATE profile SET name=$1, age=$2 WHERE id=$3 returning *`

  db, err := models.GetPostgresDb()
  if err != nil {
    panic(err))
  }
  stmt, err := db.Prepare(query)
  if err != nil {
    panic(err)
  }
  name := c.PostForm("name")
  age, _ := strconv.Atoi(c.PostForm("age"))
  id, _ := strconv.Atoi(c.Query("id"))
  err = stmt.QueryRow(name, age, id).Scan(&user.ID, &user.Name. &user.Age)

  if err != nil {
    panic(err))
  }

  c.JSON(http.StatusOK, gin.H{"status": http.StatusOK, "result": user})
}
//hàm Delete
func Delete(c *gin.Context) {
  query := `DELETE FROM profile WHERE id=$1`
  id := strconv.Atoi(c.Query("id"))
  db, err := models.GetPostgresDb()
  if err != nil {
    panic(err))
  }
  err = db.Exec(query, id)

  if err != nil {
    panic(err))
  }
  c.JSON(http.StatusOK, gin.H{"status": http.StatusOK})
}
```

Như vậy là chúng ta đã hoàn thành các hàm Create, Update, Delete.

Tiếp theo để điều khiển các hàm này chúng ta sẽ tạo ra route cho nó.

Tạo ra một thư mục có tên là `routes` trong đó có 1 file là `router.go`

Trong đó chúng ta sẽ định nghĩa khi đánh địa chỉ nào trên thanh url thì chúng ta sẽ gọi vào hàm controller nào.

```golang
package routes

import (
  "gin-app/controllers"
  "github.com/gin-gonic/gin"
  )

func NewRouter() *gin.Engine {
  router := gin.New()
  router.Use(gin.Logger())

  router.Use(gin.Recovery())

  v1 := router.Group("api")
  {
    userGroup := v1.Group("people")
    {
      userGroup.GET("/", controllers.GetPeople)
      userGroup.POST("/", controllers.Create)
      userGroup.PUT("/{id:int}", controllers.Update)
      userGroup.DELETE("/{id:int}", controllers.Delete)
    }
  }

  return router
}
```

Chỉ đơn giản như vậy thôi là chúng ta đã xử lý xong routes cho app rồi.

Tiếp theo đến `main.go` chúng ta sẽ khai báo `router.go` vào trong đó để sử dụng.

```golang
package main

import "gin-app/routes"

const port = ":8080"
func main() {
  r := routes.NewRouter()

  r.Run(port)
}
```

Tiếp theo chúng ta sẽ chạy GET `localhost:8080/api/people` để lấy hêt dữ liệu trong bản profile dưới dạng json.

POST `localhost:8080/api/people` để Create name, age cho bản ghi mới.

PUT `localhost:8080/api/people/1` để Update bản ghi đã có.

DELETE `localhost:8080/api/people/1` để Delete bản ghi đã có trong database.

Như vậy chúng ta đã cơ bản nắm được cấu trúc của Xây dựng Resful APIs cho 1 chương trình golang và nắm được cấu trúc MVC tối giản để viết Resful.

Đây là [source code](https://github.com/TuyenGa/golang-resful-api-postgres.git) của project.
Chúc các bạn thành công!