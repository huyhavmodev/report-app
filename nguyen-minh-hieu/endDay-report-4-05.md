## Nguyen Minh Hieu - 04/05

### Topic: JavaScript bất đồng bộ – Event Loop

#### 1. Stack và heap là gì?
1.1 Stack
- Stack là 1 vùng nhớ trên con chíp máy tính phục vụ cho quá trình thực thi các dòng lệnh. mỗi khi hàm được gọi thì nó sẽ đc đẩy vào 1 hàng đợi có tên là Stack.
- Stack là 1 hàng đợi kiểu LIFO (Last In First Out) nghĩa là vào đầu tiên thì ra sau cùng.
- 1 hàm chỉ đc lấy ra khỏi stack khi nó chạy xong và return.

```
        Stack    
 -------------------- 
|                    |
 -------------------- 
|      Bar           | <--
 -------------------- 
|      Foo           |
 --------------------
```

1.2 Heap
- Heap là vùng nhớ dùng để chứa kết quả phục vụ cho việc thực thi các hàm
#### 2. Event Loop là gì
- Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng 1 lúc.

- tuy js runtime chỉ có 1 thread duy nhất nhưng các webApis giúp nó giao tiếp với multi thread bên ngoài, Web apis giúp đẩy các job ra bên ngoài và chỉ tạo ra các sự kiện kèm theo các handler gắn với các sự kiện

- các Event Loop dùng để lắng nghe các Event, nhiệm vụ của event loop đó là đọc Stack và Event Queue. nếu thấy Stack rỗng nó lấy các event đầu tiên trong Event Queue và hanle gắn với event đó và đẩy vào Stack

- Event queue này khác với stack ở chỗ nó là queue kiểu FIFO (First In First Out).

- Mỗi khi có một Event được tạo ra, ví dụ user click vào một Button thì một Event sẽ được đẩy vào Event queue cùng với một handler (event listener) gắn với nó. Nếu một Event không có listener thì nó sẽ bị mất và không được đẩy vào Event queue.

``` javascript
const fs = require('fs');

function someAsyncOperation(callback) {
  // giả sử đọc file hết 95ms
  fs.readFile('/path/to/file', callback);
}

const timeoutScheduled = Date.now();

setTimeout(function logInfo() => {
  const delay = Date.now() - timeoutScheduled;
  console.log(`${delay}ms have passed since I was scheduled`);
}, 100);


// đọc file xong sẽ tiếp tục chờ thêm 10ms
someAsyncOperation(function readFileAsync() => {
  const startCallback = Date.now();

  // chờ 10ms
  while (Date.now() - startCallback < 10) {
    // do nothing
  }
});
```

