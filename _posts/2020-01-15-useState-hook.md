---
layout: "post"
title: "[Reactjs advanced] State Hook của reactjs là gì? sự khác biệt của hooks và reactjs thường."
author: tuyen
categories: [work, reactjs, tutorial]
comments: false
hidden: false
image: assets/images/reactjs/series/post-2/useStateFeature.png
---

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/series/post-2/useStateHook.png" alt="use state hook" /></p>

Chúng ta sẽ bắt đầu tìm hiểu về Hooks qua việc so sánh những dòng code trên với những ví dụ React class tương đương.

## React Class

Nếu như bạn đã dùng classes trong Reactjs trước đây, những đoạn code sau chắc hẳn trông rất quen thuộc với bạn.

```javascript
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  render() {
    return (
      <div>
        <p>You clicked {this.state.count} times</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Click me
        </button>
      </div>
    );
  }
}
```

Biến state bắt đầu với `{ count: 0 }` và ta tăng lên `state.count` khi người sử dụng click vào một button gọi đến `this.setState()`.

> <h3>Note</h3><br/> Bạn có tự hỏi rằng tại sao ta lại sử dụng một bộ counter tại đây để làm ví dụ thay thế cho rất nhiều ví dụ thực tế khác. Điều đó làm cho chúng ta tập trung vào API thay vì tiếp tục học những bước đầu tiên của Hooks.

## Hooks và Function Components

Xin được nhắc lại là Function trong React nó trông như thế này:

```javascript
const Example = () => {
  // bạn có thể sử dụng Hooks tại đây
  return <div />;
};
```

hoặc như thế này:

```javascript
function Example() {
  // bạn có thể sử dụng Hooks tại đây
  return <div />;
}
```

Hooks **không** Hoạt động trong classes. Nhưng bạn có thể dùng nó để thay thế classes.

## Hooks là gì?

Ví dụ sau đây giúp bạn thấy được cách khai báo `useState` trong reactjs:

```javascript
import React, { useState } from "react";

function Example() {
  // ...
}
```

**Vậy Hooks là gì?** Một Hook là một function đặc biệt giúp bạn `móc vào` những tính năng của React. Ví dụ, `useState` là một Hook giúp bạn thêm React state vào trong function components.

**Khi nào ta nên sử dụng Hook?** Nếu bạn viết một function component và nhận ra bạn cần phải thêm vài state cho nó, trước đây bạn phải convert nó sang class. Bây giờ bạn có thể sử dụng Hook trong function component đã được tạo ra sẵn.

## Khai báo các biến State

Trong một classes, ta thường khai báo biến `count` state với giá trị `0` bằng cách `this.state` và `{count : 0}` trong constructor:

```javascript
  class Example extends React.Component {
    constructor(props) {
      super(props);
      this.state = {
        count: 0
      };
    }
  }
```

Ở trong một function ta không hề có biến this cho nên ta không thể gọi được `this.state`. Thực tế thì ta có thể gọi trực tiếp `useState` bên trong component: 

```javascript
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
```

## Sử dụng state.

Khi muốn hiển thị ra giá trị của count trong class, ta sử dụng `this.state.count`.

```javascript
  <p>You clicked {this.state.count} times</p>
```

Trong function ta gọi trực tiếp biến `count`.

```javascript
  <p>You clicked {count} times</p>
```

## Cập nhật state.

Trong class, ta gọi `this.setState()` để cập nhật lại biến `count`.

```js
  <button onClick={() => this.setState({ count: this.state.count + 1 })}>
    Click me
  </button>
```

Trong function, ta dùng luôn hàm `setCount` và biến count để cập nhật lại chính nó mà không sử dụng `this`.

```js
  <button onClick={() => setCount(count + 1)}>
    Click me
  </button>
```

## Tóm tắt.

Bây giờ ta sẽ tóm tắt lại để kiểm tra xem ta hiểu được bao nhiêu:

```js
 1:  import React, { useState } from 'react';
 2:
 3:  function Example() {
 4:    const [count, setCount] = useState(0);
 5:
 6:    return (
 7:      <div>
 8:        <p>You clicked {count} times</p>
 9:        <button onClick={() => setCount(count + 1)}>
10:         Click me
11:        </button>
12:      </div>
13:    );
14:  }
```

- <b>Dòng 1:</b> Chúng ta import `useState` từ Hook từ React.
- <b>Dòng 4:</b> Ở trong ví dụ này, ta có một biến state mới được khai báo từ `useState` Hook. Nó trả về một cặp dữ liệu, mà ta có thể đặt tên. Chúng là biến `count` để lưu dữ liệu mà ta cần sử dụng và handler `setCount` để cập nhật lại giá trị của biến `count` đó khi nó thay đổi.
- <b>Dòng 9:</b> Khi mà ta click vào button, ta gọi đến `setCount` với một giá trị mới của `count`. React sẽ re-render lại component, và thay thế giá trị của biến count đó.

Qua bài này hi vọng mọi người có thể sử dụng được `useState` Hook của Reactjs.