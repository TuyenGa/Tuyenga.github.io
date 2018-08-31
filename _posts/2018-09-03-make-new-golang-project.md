---
layout: article
title: "Tạo một Project Go mới. CURD với Echo framework"
description: "Để tạo ra một Project mới chúng ta sử dụng go version > 1.11 có thể dễ dàng tạo ra project hơn. Và tạo ra CURD đơn giản với echo framework."
date: 2018-09-03 12:00:00  +0700
categories: [laptrinh]
tags: [blog, jekyll, github, talking, how, to, golang]
comments: true
redirect_from:
  - /tutorials/2018/09/03/make-new-golang-project/
instant_title: "develop"
instant_kicker: software
---

Làm sao để tạo ra một Project GoLang mới cho phiên bản go > 1.11.

## Tạo ra một thư mục mới và cài đặt project golang.

```cmd
mkdir golang
cd golang
touch main.go
touch go.mod

go mod init "name package"
```

Trong đó.

`mkdir golang` là để tạo ra một thư mục có tên `golang`

`cd golang` là lệnh để đi vào trong thư mục `golang`

`touch main.go` và `touch go.mod` là lệnh tạo ra 2 file `main.go` và `go.mod`

trong đó file `main.go` là file mà bạn thực hiện các thao tác để các bạn lập trình trên đó.

File `go.mod` là một phần để liên kết và lưu lại các khởi tạo mà bạn cài đặt như modules.

name package thì bạn có thể đặt tên gì cũng được hết

## Tạo ứng dụng CURD đơn giản với Go sử dụng echo framework.

**Tại sao chọn echo:** Echo framework là một framework mạnh mẽ được áp dụng fasthttp nên nhanh và dễ sử dụng hơn. Ez :))

Trước khi vào bài tôi mong bạn nên đọc và làm qua [Tour of go](https://tour.golang.org)
- Tạo ra Type cho file:

```go
type (
  Person struct {
		ID      int      `json:"id" form:"id" query:"id"`
		Name    string   `json:"name" form:"name" query:"name"`
		Age     uint     `json:"age" form:"age" query:"age"`
		Address *Address `json:"address" form:"address" query:"address"`
	}

	Address struct {
		City  string `json:"city" form:"city" query:"city"`
		State string `json:"state" form:"state" query:"state"`
	}
)
```

Trong đó Person và Address là 2 kiểu Custom type mà chúng ta tạo ra để thêm sửa xóa cho thích.

Còn `json:"id" form:"id" query:"id"` là tag để có thể convert từ struct về Json cho chúng ta.

- Khởi tạo biến `people` để sử dụng.

```go
var {
  people = map[int]*Person{}
  seq    = 1
}
```

- Khai báo Framework echo cho Project.

`"github.com/labstack/echo"`

`"github.com/labstack/echo/middleware"`

Sử dụng Echo và middleware của nó.

- Khởi tạo Router

khởi tạo router trong hàm `main()` chúng ta sẽ tạo ra các router đơn giản.

```go
func main() {
	e := echo.New()

	//Router

	e.GET("/people", GetPeople)
	e.POST("/people", CreatePerson)
	e.GET("/people/:id", GetPerson)
	e.PUT("/people/:id", UpdatePerson)
	e.DELETE("/people/:id", DeletePerson)
}
```
Sau khi tạo các router như vậy chúng ta tạo các func tương ứng.

```go
func GetPeople(ctx echo.Context) error {}
func CreatePerson(ctx echo.Context) error {}
func GetPerson(ctx echo.Context) error {}
func UpdatePerson(ctx echo.Context) error {}
func DeletePerson(ctx echo.Context) error {}
```

- Tiếp theo Khởi tạo server.

```go
func main() {
	e := echo.New()

	e.Use(middleware.Logger())
	e.Use(middleware.Recover())

	//Router

	e.GET("/people", GetPeople)
	e.POST("/people", CreatePerson)
	e.GET("/people/:id", GetPerson)
	e.PUT("/people/:id", UpdatePerson)
	e.DELETE("/people/:id", DeletePerson)

	//PORT
        PORT := ":8080"

        // Server
	e.Logger.Fatal(e.Start(PORT))
}
```

- **Created**

```go
func CreatePerson(ctx echo.Context) error {
  u := &Person{
    ID: seq,
  }

  if err := ctx.Bind(u); err != nil {
    return err
  }
  people[u.ID] = u
  seq ++

  return ctx.JSON(http.StatusCreated, u)
}
```

Chúng ta khởi tạo biến u là một kiểu Person và có sẵn ID = seq.

Tiếp theo sẽ Bind(u) tức là sẽ lấy các giá trị có dạng post mà chúng ta gửi lên gán vào u

Tiếp theo chúng ta sẽ tìm trong people giá trị có id = u. ID và gán nó bằng u

seq tăng thêm 1 giá trị.

Trả về JSON.

- **UPDATE**

```go
func UpdatePerson(ctx echo.Context) error {
	u := new(Person)

	if err := ctx.Bind(u); err != nil {
		return err
	}
	id, _ := strconv.Atoi(ctx.Param("id"))
	people[id] = u
	people[id].ID = id
	return ctx.JSON(http.StatusOK, people[id])
}
```
Ở đây Giống như với Create Update sẽ tạo ra một biến u được gán bằng new Person.

Sau đó Bind vào biến đó giá trị của những dữ liệu chúng ta gửi lên.

Lấy ID và convert về `int` thông qua hàm Atoi của strconv.

gán trở lại ID là chúng ta đã hoàn thành.

- **Read**

Read ở đây là hiển thị ra list data hoặc từng thành phần một.

*Hiển thị list data*

```go

func GetPeople(ctx echo.Context) error {
	return ctx.JSON(http.StatusOK, people)
}
```
*Hiển thị chi tiết từng phần tử*
```go
func GetPerson(ctx echo.Context) error {
	id, _ := strconv.Atoi(ctx.Param("id"))
	return ctx.JSON(http.StatusOK, people[id])
}
```

Sự khác biệt của 2 hàm này là id.

Hàm chi tiết cần phải biết id để có thể hiển thị ra đúng phần tử cần sử dụng.

Còn hàm GetPeople thì không cần quan tâm id chỉ cần show hết các phần tử ra.

- **Delete**

```go
func DeletePerson(ctx echo.Context) error {
	id, _ := strconv.Atoi(ctx.Param("id"))

	delete(people, id)
	return ctx.NoContent(http.StatusNoContent)
}
```

Tổng kết lại chúng ta có.
```go
package main

import (
	"net/http"
	"strconv"

	"github.com/labstack/echo"
	"github.com/labstack/echo/middleware"
)

type (
	Person struct {
		ID      int      `json:"id" form:"id" query:"id"`
		Name    string   `json:"name" form:"name" query:"name"`
		Age     uint     `json:"age" form:"age" query:"age"`
		Address *Address `json:"address" form:"address" query:"address"`
	}

	Address struct {
		City  string `json:"city" form:"city" query:"city"`
		State string `json:"state" form:"state" query:"state"`
	}
)

var (
	people = map[int]*Person{}
	seq    = 1
)

func main() {
	e := echo.New()

	e.Use(middleware.Logger())
	e.Use(middleware.Recover())

	//Router

	e.GET("/people", GetPeople)
	e.POST("/people", CreatePerson)
	e.GET("/people/:id", GetPerson)
	e.PUT("/people/:id", UpdatePerson)
	// e.DELETE("/people/:id", DeletePerson)

	//PORT
	PORT := ":8080"
	e.Logger.Fatal(e.Start(PORT))
}

func GetPeople(ctx echo.Context) error {
	return ctx.JSON(http.StatusOK, people)
}

func CreatePerson(ctx echo.Context) error {
	u := &Person{
		ID: seq,
	}

	if err := ctx.Bind(u); err != nil {
		return err
	}
	people[u.ID] = u
	seq++

	return ctx.JSON(http.StatusCreated, u)
}

func GetPerson(ctx echo.Context) error {
	id, _ := strconv.Atoi(ctx.Param("id"))
	return ctx.JSON(http.StatusOK, people[id])
}

func UpdatePerson(ctx echo.Context) error {
	u := new(Person)

	if err := ctx.Bind(u); err != nil {
		return err
	}
	id, _ := strconv.Atoi(ctx.Param("id"))
	people[id] = u
	people[id].ID = id
	return ctx.JSON(http.StatusOK, people[id])
}

func DeletePerson(ctx echo.Contetx) error {
	id, _ := strconv.Atoi(ctx.Param("id"))

	delete(people, id)
	return ctx.NoContent(http.StatusNoContent)
}
```

Như vậy cơ bản chúng ta đã hoàn thành 1 phần của việc học golang. Ngoài làm theo hướng dẫn các bạn có thể tìm sách về golang để tham khảo thêm.
Chúc các bạn thành công.