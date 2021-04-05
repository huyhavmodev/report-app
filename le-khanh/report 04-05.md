# **_Promise API_**

- `promise.all` nhận vào một mảng các promise và trả về một mảng các kết quả sau khi các promise trong mảng được thực thi hết và trả về `fullfill`. syntax:
  ```javascript
  let promise = Promise.all([...promises...]);
  ```
  - Ví dụ:
  ```javascript
  Promise.all([
    new Promise((resolve) => setTimeout(() => resolve(1), 3000)), // 1
    new Promise((resolve) => setTimeout(() => resolve(2), 2000)), // 2
    new Promise((resolve) => setTimeout(() => resolve(3), 1000)), // 3
  ]).then(alert); // 1,2,3
  ```
  - Trong ví dụ trên, promise sẽ có kết quả sau 3s và mảng kết quả là `[1,2,3]`, thứ tự của `result` là thứ tự của `promise` trong mảng, bất kể `promise` đó mất nhiều thời gian hơn để thực hiện.
  - Nếu một `promise` trong mảng bị `rejected`, ngay lập tức `promise.all` sẽ được trả về là `rejected`.
- `promise.allSettled`, giống với `promise.all` nhưng trả về kết quả khi tất cả các `promise` settled (thay đổi state), bất kể đó là `fullfill` hay `rejected`.
- `promise.race` giống với `promise.allSettled` nhưng thay vì trả về một mảng kết quả thì nó trả về `promise` nào `settled` đầu tiên và kết quả của nó
- `promise.any` giống với `promise.race` nhưng sẽ trả về promise nào `fullfill` đầu tiên và kết quả của nó, nếu không có promise nào `fullfill` thì nó trả về `AggregateError` là một `error object` đặc biệt lưu tất cả các lỗi của promise trong thuộc tính `errors` của nó.
- `promise.resolve/rejected`,
  - `promise.resolve(value)` tạo một `resolve promise` với kết quả là `value`. Giống với:
    ```javascript
    let promise = new Promise((resolve) => resolve(value));
    ```
  - `promoise.rejected(error)` tạo một `rejected promise` với `error`. Giống với:
    ```javascript
    let promise = new Promise((resolve, rejected) => rejected(error));
    ```
