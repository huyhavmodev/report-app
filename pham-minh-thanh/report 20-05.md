- Hiểu về các server sử dụng git
- Tìm hiểu vắn tắt nội dung về git
- Làm bài tập về git thông qua file git.practice

- JS test (100%)
  https://codesandbox.io/s/js-test-forked-w5tdf
- Environment: Nodejs and npm
 - NodeJS là một nền tảng được xây dựng trên V8 JavaScript Engine – trình thông dịch thực thi mã JavaScript, giúp xây dựng các ứng dụng web một cách đơn giản và dễ dàng mở rộng. Nó là môi trường chạy code js ở server.
 - npm là Node Package Manager đi kèm và hỗ trợ từng bản phát triển của Node. Trong nhiều năm, Node được các lập trình viên JavaScript sử dụng rộng rãi để chia sẻ công cụ, cài đặt nhiều mô-đun khác nhau và quản lý dependency. Hãy cùng tìm hiểu sâu hơn về npm là gì và cách thức hoạt động của nó. Nó rất quan trọng với những ai làm việc với Node.js.
 - Event Loop
  + Call stack
  + Webapis
  + Callback Queue

- API and Authentication concept
 
  HTTP Request (OPTIONS, GET, POST, PUT, PATH, DELETE)
  - OPTIONS:
  - GET: LẤY DATA VỀ
  - POST: TẠO DATA
  - PUT: SỬA ĐỔI DATA
  - PATH: SỬA ĐỔI DATA
  - DELETE: XÓA DATA
  CORS issue - Cross-Origin Resource Sharing
  - Origin = Protocol(http/https) + Domain + Port
  - Khác 1 trong 3 thứ thì nằm trên Origin khác. Điều này sẽ không cho phép client khác Origin tương tác, lấy dữ liệu từ server. 
  - Cách giải quyết là xử lý ở server
  

  Authentication/Authorization
  - Authentication: Xác thực 
  - Xác nhận đúng người dùng hợp lệ mới được đăng nhập vào hệ tống
  - Diễn ra trước 
  - Sử dụng password, OTP, PIM, 2fa
  - Authorization: Phân quyền
  - Kiểm tra người dùng đó có quyền thực hiện hay truy cập trang web này không.
  - Diễn ra sau khi authentication thành công
  - Sử dụng JWT để thực hiên permissions
  JSON web token (JWT)
  - Phân biệt Token(staleful) và Cookie(staleful):
    Cookie:
    + Stateful server
    + Hard to achieve
    + Controlled by serrver(luu cac seasion trong database)
    + Perfomance : Bad
    + Mobile ready: No
    + Size : tiny

    Token:
    + Stateless server
    + Easy to scale
    + Controller by Client (Thường trong Local Storage)
    + Size: can be large as your data grow (trường hợp thực tế, lưu quá nhiều trường vào JWT đâm ra sẽ bị lỗi)
    + Use JWT
  - JWT:
  - Gồm 3 phần: 
    - HEADER
    - PAYLOADKEY 
    - SECRET
    => VERIFY TOKEN (Sinh ra ở authencation server và được gửi cho client, được gửi kèm theo request lên application server mỗi lân thực thi - trong phần Header)
    - Ngoài hàm Sinh token(có thời gian tồn tại) ta cần phải có hàm RefreshToken để refresh khi gần hết thời gian (Subsiy có sử dụng)

  RESTful vs GraphQL concept

  - Resful là chuẩn viết API dựa vào HTTP request. Các methods như : get, post, put, patch, delete
  - GraphQL là chuẩn viết API kiểu mới.



  Postman
  - Tool để test API
