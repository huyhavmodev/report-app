## TRAN DAI MINH 08-11

## TOPIC: LTS, Event Loop, Authentication/Authorization, JSON web token (JWT), Basic concepts of web applications, how they work and the HTTP protocol.

- LTS (Long Term Support) nghĩa là phiên bản được hỗ trợ dài hạn.

- Event Loop

  - Stack là môt vùng nhớ đặc biệt trên con chip máy tính phục vụ cho quá trình thực thi các dòng lệnh, mỗi khi một hàm được gọi thì nó sẽ được đẩy vào một stack (hàng đợi).
  - Heap là vùng nhớ được dùng để chưa kết quả tạm phục vụ cho việc thực thi các hàm trong stack.
  - Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model).
  - Tuy Js Runtime chỉ có một thread duy nhất nhưng các web apis giúp nó giao tiếp với thế giới multi thread bên ngoài.
  - Web apis giúp đẩy các job ra bên ngoài và chỉ tạo ra các sự kiện kèm theo các handler gắn với các sự kiện.
  - Nhiệm vụ của Event Loop rất đơn giản đó là đọc Stack và Event Queue. Nếu nhận thấy Stack rỗng nó sẽ nhặt Event đầu tiên trong Event Queue và handler (callback hoặc listener) gắn với Event đó và đẩy vào Stack.

```js
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

- Authentication/Authorization

  - Authentication là về việc xác thực thông tin đăng nhập của người dùng như Tên người dùng / ID người dùng và mật khẩu để xác minh danh tính của người dùng.

  - Authorization nghĩa là sau khi xác nhận authentication, thì hệ thống sẽ xác nhận quyền truy cập của account đó ở mức độ nào.

- JSON web token (JWT) là một chuẩn mở (RFC 7519) định nghĩa một cách nhỏ gọn và khép kín để truyền một cách an toàn thông tin giữa các bên dưới dạng đối tượng JSON. Thông tin này có thể được xác minh và đáng tin cậy vì nó có chứa chữ ký số. JWTs có thể được ký bằng một thuật toán bí mật (với thuật toán HMAC) hoặc một public / private key sử dụng mã hoá RSA.

  - Cấu trúc của JWT:

  ```
  <base64-encoded header>.<base64-encoded payload>.<base64-encoded signature>
  ```

  - Header bao gồm hai phần chính: loại token (mặc định là JWT - Thông tin này cho biết đây là một Token JWT) và thuật toán đã dùng để mã hóa (HMAC SHA256 - HS256 hoặc RSA).

  - Payload chứa các claims. Claims là một các biểu thức về một thực thể (chẳng hạn user) và một số metadata phụ trợ. Có 3 loại claims thường gặp trong Payload: reserved, public và private claims.

  - Signature trong JWT là một chuỗi được mã hóa bởi header, payload cùng với một chuỗi bí mật theo nguyên tắc sau:

```
HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)
```

- Basic concepts of web applications, how they work and the HTTP protocol.

  - Thành phần cơ bản của web: domain, web hosting, source code.
