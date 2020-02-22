---
layout: "post"
title: "[Mobx State Tree] Mobx, mobx-state-tree? Làm sao để lấy dữ liệu từ APIs trong mobx-state-tree?"
author: tuyen
categories: [work, reactjs, mobx-state-tree, shared]
comments: false
hidden: false
image: assets/images/reactjs/mobx/mobx-state-tree.jpg
---

Mobx là một thư viện được tạo ra để quản lý state trở nên đơn giản hơn và có thể dễ dàng mở rộng hơn.

Sau đây là quy trình hoạt động của mobx.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/mobx/flow.png" alt="mobx flow" /></p>

Mobx cùng với reactjs thực sự là một sự kết hợp mạnh mẽ. React renders các state của ứng dụng bằng cách cung cấp các cơ chế để dịch nó vào bên trong các components. Mobx cung cấp cơ chế lưu trữ và cập nhật trạng thái ứng dụng để sau đó React có thể sử dụng.

`mobx-state-tree` là một state container kết hợp được tính đơn giản và dễ dàng của dữ liệu và có thể thay đổi với khả năng truy cập dữ liệu để dễ dàng cập nhật của các dữ liệu quan sát được.

### tree = type + state

Mỗi **node** trong tree đều được mô tả bởi 2 thứ: đó là **types** và **data**.

Một ví dụ đơn giản nhất của `mobx-state-tree` như sau:

```javascript
import { types } from "mobx-state-tree";

// declaring the shape of a node with the type `Todo`
const Todo = types.model({
  title: types.string
});

// creating a tree based on the "Todo" type, with initial data:
const coffeeTodo = Todo.create({
  title: "Get coffee"
});
```

Như vậy cơ bản là một **tree** sẽ có **types** và **data**. **types** là để định danh `tree` còn **data** là giá trị của **tree** đó.

Bài viết hôm nay chủ yếu là để nói về làm sao để gán được **data** cho `tree` trong một dự án thực tế.

### Fetch Data từ một APIs.

Tôi sẽ không nói chi tiết làm sao để fetch được data mà nói cách khai báo **types** và gán **data** cho `tree`.

Cho một dữ liệu giả sau khi fetch như sau:

```json
{
  "data": [
    {
      "id": "D02DEBF8fsd",
      "enterprise": {
        "name": "TNHH h C.L",
        "code": "03039323"
      },
      "state": "approve",
      "created_at": "2020-01-14T07:16:59Z",
      "contact_name": "Pham Minh Ngoc",
      "contact_mobile": "0972736308",
      "amount": 100000000,
      "area": ["1", "2", "3"]
    },
    {
      "id": "6F0BBEE3",
      "enterprise": {
        "name": "TNHH Knh C.L",
        "code": "03030323"
      },
      "state": "approve",
      "created_at": "2020-01-08T03:12:45Z",
      "contact_name": "Ngoc",
      "contact_mobile": "0972736308",
      "amount": 100000,
      "area": ["1", "2", "3"]
    }
  ]
}
```

Đầu tiên để fetch được **data** thì ta phải phân tích được **types** của nó. Data này là một array bao gồm nhiều object. nên đầu tiên ta tạo ra object đó trước và đặt tên nó là `file`

```javascript
// sử dụng types của mobx state tree
// ta sẽ defind toàn bộ kiểu của các keys trong object đó và khai báo nó.
types.models("file", {
  id: types.string, // id của file là một kiểu string
  state: types.string,
  created_at: types.string,
  contact_name: types.string,
  contact_mobile: types.string,
  amount: types.number,
  enterprise: types.optional(enterprise, {}), // enterprise là một object khác nên ta lại defind nó ra ngoài để dễ quản lý hơn.
  area: types.optional(types.array(types.string), []) // kiểu array mà chỉ có string hoặc thì để types.array thôi
});

types.models("enterprise", {
  name: types.string,
  code: types.string
});
```

Như vậy ta đã defind xong object của data. Tiếp theo ta sẽ tạo ra một **models** để có thể gán **data** cho **types** mà ta đã defind trước đó.

```javascript
types.models("data", {
    files: types.optional(types.array(file), []) // types.optional là một kiểu dữ liệu đặc biệt lựa chọn một trong 2. nên ta thường để default data cho các dữ liệu required.
})
```

Như vậy ta đã biết được cách defind **types** và **data** trong `tree` của `mobx-state-tree` như thế thì dù dữ liệu có nhiều hay phức tạp như thế nào ta cũng có thể defind và fetch nó từ APIs về để sử dụng trong project Reactjs của mình thông qua `mobx-state-tree`.