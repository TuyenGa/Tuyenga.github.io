---
layout: "post"
title: "[Reactjs advanced] Sử dụng reactjs Hook"
author: tuyen
categories: [work, reactjs, tutorial]
comments: false
hidden: false
image: assets/images/reactjs/series/post-1/featureImage.jpeg
---

Hook là một nâng cấp trong React 16.8. Họ khuyến cáo nên sử đụng state và các tính năng mới thay vì viết ES6 classes.

## React hook là gì?

Theo như tên gọi của nó thì có thể hiểu sơ qua **Hook** là một cái móc câu có thể câu biến và dữ liệu ta cần ra để sử dụng ngay mà không cần thông qua trung gian như props nữa.

Thực tế thì hook là một function cho phép bạn kết nối vào trong React state và tính năng lifecycle từ các function component. Nó không hoạt động trong ES6 classes.

## State Hook

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/series/post-1/useState.png" alt="use state hook" /></p>

Trên đây là `useState` là một hook của reactjs. Được gọi trong function component, Ở đây useState() trả về một cặp dữ liệu. Thứ nhất là một local state hiện tại được khai báo khi khởi tạo hook. Thứ 2 đó là một handler cho phép bạn thay đổi local state đó cái này giống như `this.State` được sử dụng trong ES6 class trước đó.

#### Khai báo nhiều biến local state.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/series/post-1/multiState.png" alt="multi state hook" /></p>

Kiểu khai báo array destructuring để ta khai báo nhiều tên khác nhau cho các biến local state bằng cách sử dụng `useState`. Những tên này không thuộc về `useState` API. Thực tế ta có thể React giả định rằng nếu bạn gọi nhiều lần `useState`. Bạn sẽ nhận được đúng như thứ tự mà bạn đã khai báo trong mọi lần render lại component.

## Effect Hook

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/series/post-1/useEffect.png" alt="useEfect" /></p>

Sử dụng `useEffect` cho phép ta tiếp cận với feature React lifecycle. Hook này tương tự như gộp 3 lifecycle của React là `componentDidMount`, `componentDidUpdate` và `componentWillUnmount` nhưng được gom và viết lại thành một function duy nhất đó là `useState`.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/reactjs/series/post-1/using-useEffect.png" alt="using useEffect" /></p>

Ở đây `useEffect` kiêm luôn 3 nhiệm vụ của 3 `componentDidMount`, `componentDidUpdate` và cả `componentWillUnmount`. Trong đó callback của useEffect sẽ có nhiệm vụ là `componentDidMount` và `componentDidUpdate`. Hàm return cuối cùng giống như `componentWillUnmount` hàm này có nhiệm vụ clear `componentDidMount` trong callback đó.

## ✌️ Các quy tắc sử dụng hooks.

Hooks là các javascript function nhưng chúng có áp dụng thêm 2 quy tắc sử dụng.

- Gọi hooks đầu tiên. Không gọi hooks trong vòng lặp, điều kiện hoặc hàm lồng nhau.

- Gọi Hooks từ React function components. Không gọi từ javascript function mặc định.

Để dễ dàng hơn trong việc imporve hooks ta có thể cài đặt plugin [eslint-plugin-react-hooks](https://www.npmjs.com/package/eslint-plugin-react-hooks) nó sẽ tự động cảnh báo và giúp bạn hiểu hơn về các quy tắc sử dụng React Hooks.

## 💡Xây dựng Hooks của riêng bạn.

Thỉnh thoảng, tôi muốn sử dụng lại một số trạng thái logic ở trong các components. Bình thường, thì có 2 cách phổ biến để giải quyết vấn đề này: Higher-order components và render props. Nhưng bây giờ bạn có thể tuỳ biến hooks để giải quyết vấn đề này, nhưng không cần phải thêm các components trong dự án của bạn.

Ở trên tôi đã giới thiệu với bạn một FriendStatus component nó gọj `useState` và `useEffect` Hooks để theo dõi trạng thái online của người bạn nào đó. Để tôi nói cho bạn biết logic của quá trình đó trong một component khác.

Đầu tiên, Ta sẽ tách logic này thành một custom Hook gọi là `useFriendStatus`:

```javascript
import React, { useState, useEffect } from "react";

function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  useEffect(() => {
    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}
```

Tôi sẽ lấy `friendID` từ argument, và trả về liệu người bạn của chúng ta có đang online.

Bây giờ chúng ta sử dụng nó trong cả 2 components:

```javascript
function FriendStatus(props) {
  const isOnline = useFriendStatus(props.friend.id);

  if (isOnline === null) {
    return "Loading...";
  }
  return isOnline ? "Online" : "Offline";
}
```

```javascript
function FriendListItem(props) {
  const isOnline = useFriendStatus(props.friend.id);

  return (
    <li style={{ color: isOnline ? "green" : "black" }}>{props.friend.name}</li>
  );
}
```

Các trạng thái của các components này là hoàn thoàn đọc lập. Hooks là một các tái sử dụng các trạng thái logic. Thực tế thì, việc gọi một hook hoàn toàn độc lập nên ta có thể gọi cùng một hook nhiều lần trong một component.

Các Hook tuỳ chỉnh là nhiều quy ước hơn là tính năng. Nếu tên của một function bắt đầu với `use` và gọi các hook khác, ta có thể gọi nó là custom hook. `useSomething` cách đặt tên quy ước của hooks.

Bạn có thể viết custom Hooks bao gồm nhiều trường hợp giống như xử lý form, animation, timer, và nhiều biến khác. Hi vọng các bạn có thể tự xây dựng được những custom hook để xử lú các vấn đề của riêng mình.
