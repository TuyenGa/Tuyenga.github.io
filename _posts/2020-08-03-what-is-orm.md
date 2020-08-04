---
layout: post
title: "ORM là gì?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap, ORMs, Object, database, mapping]
image: assets/images/roadmap/ORM/ormapping.png
---
**ORM (Object-Relational Mapping)** là một kỹ thuật lập trình để chuyển đổi dữ liệu giữa các cơ sở dữ liệu quan hệ và các ngôn ngữ lập trình hướng đối tượng như Java, C# ... Một hệ thống ORM có những ưu điểm sau:

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/ORM/uu-diem.png" alt="Ưu điểm của hệ thống ORM" /></p>

Một giải pháp ORM bao gồm các thực thể sau:

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/ORM/giai-phap-khac-phuc.png" alt="Một số giải pháp" /></p>


## Java ORM Framework

Có một số persistent framework và các tuỳ chọn ORM trong Java. Một Framework là một dịch vụ ORM lưu và truy xuất các Object vào một cơ sở dữ liệu quan hệ.

- Enterprise JavaBeans Entity Beans
- Java Data Objects
- Castor
- TopLink
- Spring DAO
- Hibernate
- And many more

## Tại sao lại sử dụng ORM (Object-Relational Mapping)

Khi chúng ta làm việc với một hệ thống **OOP,** có một sự không khớp giữa mô hình đối tượng và cơ sở dữ liệu quan hệ. RDBMS thể hiện dữ liệu trong một định dạng bảng, trong khi các ngôn ngữ hướng đối tượng thể hiện nó như một đồ thị kết nối của các Object. Xem xét lớp Java sau đây với constructor phù hợp và phương thức public liên quan:

```java
public class Employee {
   private int id;
   private String first_name; 
   private String last_name;   
   private int salary;  
 
   public Employee() {}
   public Employee(String fname, String lname, int salary) {
      this.first_name = fname;
      this.last_name = lname;
      this.salary = salary;
   }
   public int getId() {
      return id;
   }
   public String getFirstName() {
      return first_name;
   }
   public String getLastName() {
      return last_name;
   }
   public int getSalary() {
      return salary;
   }
}
```

Các đối tượng trên cần phải được lưu trữ và truy xuất vào bảng RDBMS sau:

```sql
create table EMPLOYEE (
   id INT NOT NULL auto_increment,
   first_name VARCHAR(20) default NULL,
   last_name  VARCHAR(20) default NULL,
   salary     INT  default NULL,
   PRIMARY KEY (id)
);
```

Vấn đề đầu tiên, nếu ta cần phải sửa đổi thiết kế cơ sở dữ liệu của chúng ta sau khi đã phát triển một vài trang của website hoặc ứng dụng? Thứ hai, việc tải và lưu trữ các đối tượng trong một cơ sở dữ liệu quan hệ làm cho chúng ta gặp một số vấn đề không khớp.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/ORM/cac-van-de.png" alt="Các vấn đề không khớp giữa Ngôn ngữ lập trình và RADBMS" /></p>

**ORM (Object Relational Mapping)** là một giải pháp giải quyết các vấn đề trên.