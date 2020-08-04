---
layout: post
title: "ORM là gì?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, ORMs, Object, database, mapping]
image: assets/images/roadmap/ORM/hibernate.png
---

Hibernate ra đời năm 2001 bởi nhà sáng lập Gavin King như một sự thay thế cho EJB2 kiểu thực thể Bean. Hiện nay, phiên bản mới nhất của Hibernate là Hibernate ORM 5.4.19.Final.

## Hibernate là gì?

Hibernate là một giải pháp ORM mã nguồn mở, gọn nhẹ. Hibernate giúp đơn giản hoá sự phát triển của ứng dụng java để tương tác với cơ sở dữ liệu.

Tool ORM giúp đơn giản hoá việc tạo ra, thao tác và truy cập dữ liệu. Đó là một kỹ thuật lập trình để ánh xạ đối tượng được lưu trữ vào trong cơ sở dữ liệu.

## Lợi ích của việc sử dụng Hibernate

Hibernate Framework có một số lợi ích sau đây:

1.  **Mã nguồn mở gọn nhẹ:** Nó là mã nguồn mở có giấy phép LGPL.
2. **Hiệu xuất nhanh:** Hiệu xuất của nó nhanh bởi vì bộ nhớ cache được sử dụng bên trong Hibernate Framework. Có hai loại bộ nhớ cache trong Hibernate bao gồm bộ nhớ cache cấp một và bộ nhớ cache cấp 2.
3. **Truy vấn cơ sở dữ liệu độc lập:** HQL(Hibernate Query Language) là phiên bản hướng đối tượng cuẩ SQL. Nó tạo ra các truy vấn cơ sở dữ liệu độc lập. Vì vậy, không cần phải viết các truy vấn cơ sở dữ liệu cụ thể. Trước Hibernate, nếu có dự án có cơ sở dữ liệu bị thay đổi, ta cần phải thay đổi truy vấn trên SQL dẫn đến sự cố bảo trì.
4. **Tạo bảng tự động:** Hibernate cung cấp phương tiện để tạo ra các bảng cơ sở dữ liệu tự động. Vì vậy, không cần phải tạo ra các bảng trong cơ sở dữ liệu bằng tay.
5. **Đơn giản lệnh join phức tạp:** Có thể lấy dữ liệu từ nhiều bảng một cách dễ dàng với Hibernate.
6. **Cung cấp thống kê truy vấn và trạng thái cơ sở dữ liệu:** Hibernate hỗ trợ bộ nhớ cache truy vấn và cung cấp số liệu thống kê về truy vấn và trạng thái của cơ sở dữ liệu.

## Các Database được hỗ trợ

Hibernate hỗ trợ hầu hết tất cả các Database chính. Dưới đây là danh sách vài cơ sở dữ liệu quan hệ được hỗ trợ bởi Hibernate.

- HSQL Database Engine
- DB2/NT
- MySQL
- PostgreSQL
- FrontBase
- Oracle
- Microsoft SQL Server Database
- Sybase SQL Server
- Informix Dynamic Server

## Các công nghệ được hỗ trợ

Hibernate hỗ trợ nhiều công nghệ bao gồm:

- XDoclet Spring
- J2EE
- Eclipse plugins
- Maven

Trên đây là tổng quan cơ bản về Hibernate Framework. Bài viết này cung cấp cho bạn về lợi ích, Database, Công nghệ được ORM Hibernate hỗ trợ.

Hướng dẫn chi tiết về [Hibernate](https://www.tutorialspoint.com/hibernate/index.htm)