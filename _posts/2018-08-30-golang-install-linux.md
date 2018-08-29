---
layout: article
title: "Cài đặt Golang trên hệ điều hành Ubuntu"
description: "Golang là một ngôn ngữ mạnh mẽ và dễ dàng học. Hôm nay chúng ta sẽ cài đặt Golang trên Ubuntu 16.04"
date: 2018-08-30 12:00:00  +0700
categories: [Learn live]
tags: [blog, jekyll, github, talking, how, to,]
comments: true
redirect_from:
  - /tutorials/2018/04/02/install-golang-in-linux/
instant_title: "Live to learn"
instant_kicker: Live
---

Golang là một ngôn ngữ mạnh mẽ và dễ dàng học. Hôm nay chúng ta sẽ cài đặt Golang trên Ubuntu 16.04

## Tải golang cho ubuntu.

Đầu tiên để có thể cài đặt golang thì chúng ta phải tải nó về trước.
Ở đây sẽ có rất nhiều phiên bản dành cho các hệ điều hành khác nhau. Các bạn nhớ download đúng phiên bản dành cho hệ điều hành của mình [tại đây](https://golang.org/dl/).

Sau khi download thì file của bạn sẽ có dạng go$VERSION.$OS-$ARCH.tar.gz như vậy là chúng ta đã thành công.

## Giải nén và cài đặt cơ bản.

Chúng ta sẽ phải giải nén file .tar.gz vào thư mục /usr/local, tạo ra cây thư mục Go trong /usr/local/go. Ví dụ

```cmd
tar -C /usr/local -xzf go$VERSION.$OS-$ARCH.tar.gz
```
Nếu hệ điều hành của bạn không cấp quyền thì thêm `sudo` đằng trước câu lệnh trên.

Trong đó $OS là hệ điều hành của bạn, $ARCH là số bit của hệ điều hành đó. vd linux x86 hoặc x64

Tiếp theo chúng ta sẽ phải dùng lệnh

```
nano $HOME/.profile
```

Thêm đoạn code sau vào dưới cuối của file .profile

```
export GOROOT=/usr/local/go
export GOPATH="$HOME/.dotfiles/go-lang"
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOROOT/bin:$GOBIN
```

**Note:** thay đổi file profile có thể không áp dụng cho lần tiếp theo bạn nâng cấp phiên bản cho golang.