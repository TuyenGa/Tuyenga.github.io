---
layout: "post"
title: "[Reactjs nâng cao series] Xây dựng một dự án nhỏ với Reactjs"
author: tuyen
categories: [work, reactjs, tutorial]
comments: false
hidden: false
image: assets/images/reactjs/series/post-1/featureImage.jpeg
---

Reactjs là cái gì? Có những cách nào để xây dựng một webapp lớn và nhanh bằng javascript.

Một trong những điều quan trọng nhất của Reactjs là làm sao để bạn dùng nó để xây dựng lên các ứng dụng hoặc webapp. Ở bài viết này sẽ đi xuyên suốt quá trình làm sao để xây dựng một ứng dụng search sản phẩm cơ bản sử dụng reactjs.

## Bắt đầu với các dữ liệu giả.

Để xây dựng project cơ bản này cần phải có những dữ liệu JSON API giống như thế này:


<p style="margin: 0 auto;"><img src="{{ site.baseurl }}/assets/images/reactjs/series/post-1/mock.png" alt="mock" width="200"/></p>

Với mock trên ta xây dựng được dữ liệu như sau.

```js
[
  {category: "Sporting Goods", price: "$49.99", stocked: true, name: "Football"},
  {category: "Sporting Goods", price: "$9.99", stocked: true, name: "Baseball"},
  {category: "Sporting Goods", price: "$29.99", stocked: false, name: "Basketball"},
  {category: "Electronics", price: "$99.99", stocked: true, name: "iPod Touch"},
  {category: "Electronics", price: "$399.99", stocked: false, name: "iPhone 5"},
  {category: "Electronics", price: "$199.99", stocked: true, name: "Nexus 7"}
];
```
