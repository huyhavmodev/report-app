## Nguyen Minh Hieu - 04/01


### Topic: Promise Là gì?

### 1. Promise là gì?
- là 1 cơ chế trong js giúp thực thi các thao tác bất đồng bộ mà không bị Callback hell. các tác vụ bất đồng bộ là AJAX request, gọi hàm bên trong setTimeout,setInterval, requestAnimationFrame, …
- Dưới đây là một callback hell điển hình.
```
api.getUser('pikalong', function(err, user) {
  if (err) throw err
  api.getPostsOfUser(user, function(err, posts) {
    if (err) throw err
    api.getCommentsOfPosts(posts, function(err, comments) {
      // vân vân và mây mây...
    })
  })
})
```
Khi dùng với Promise:

```javascript
api.getUser('pikalong')
  .then(user => api.getPostsOfUser(user))
  .then(posts => api.getCommentsOfPosts(posts))
  .catch(err => { throw err })

```
tạo 1 promise obj:
```javascript
const p = new Promise( (resolve, reject) => {
  // Thực thi các tác vụ bất đồng bộ ở đây, và gọi `resolve(result)` khi tác
  // vụ hoàn thành. Nếu xảy ra lỗi, gọi đến `reject(error)`.
})
```
Trong đó, executor là một hàm có hai tham số:
* resolve là hàm sẽ được gọi khi promise hoàn thành
* reject là hàm sẽ được gọi khi có lỗi xảy ra

- Nếu hàm resolve được gọi, trạng thái của promise sẽ là thành công và hành động .then được gọi. Tham số bạn truyền vào hàm resolve sẽ được chuyển đến then:
```javascript
const promise = new Promise((resolve, reject) => {
  // Note: resolve chỉ cho phép truyền đúng 1 param
  return resolve(27)
})

// Tham số  từ resolve sẽ được chuyển đến then.
promise.then(number => console.log(number)) // 27
```
- Ngược lại nếu hàm reject được gọi, trạng thái của promise sẽ là thất bại và hành động catch được gọi. Tương tự như resolved tham số được truyền vào reject sẽ được chuyển đến catch.
``` javascript
const promise = new Promise((resolve, reject) => {
  // Note: reject chỉ cho phép truyền đúng 1 param
  return reject('lỗi')
})

promise.catch(err => console.log(err)) // lỗi
```