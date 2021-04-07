# API - restful conventions and practics

## GET:

_Thường dùng để lấy một tập hợp hoặc một bản ghi nhất định_

```javascript
import axios from "axios";
// retrive list post
axios.get("https://jsonplaceholder.typicode.com/posts");
// or one post
axios.get("https://jsonplaceholder.typicode.com/posts/1");
```

## POST

_Thường dùng để thêm 1 bản ghi_

```javascript
import axios from "axios";
// retrive list post
axios.post("https://jsonplaceholder.typicode.com/posts", {
  // add a post
  id: 999,
  title: "title..",
});
```

## DELETE

_Thường dùng để xóa một bản ghi_

```javascript
// delete post id = 1
axios.delete("https://jsonplaceholder.typicode.com/posts/1");
```

## PUT

_Thường dùng để update hoàn toàn 1 bản ghi_

```javascript
// update bản ghi có id là 1 thành bản ghi mới
axios.put("https://jsonplaceholder.typicode.com/posts/1", {
  id: 2,
  title: "new title",
});
```

## PATCH

_Thường dùng để update/ thay thế 1 phần của bản ghi_

```javascript
// update title của bản ghi có id là 1
axios.patch("https://jsonplaceholder.typicode.com/posts/1", {
  title: "new title",
});
```
