# NGUYỄN THÀNH LUÂN - Report 08/10:

**Cors Issue**
- Cors (Cross-origin resource sharing): chia sẻ tài nguyên chéo. Là cơ chế cho phép nhiều tài nguyên khác nhau của 1 trang web có thể được truy vấn từ domain khác với 
domain của trang đó.
    + Cors: còn là chính sách của trình duyệt ngăn chặn việc truy cập tài nguyên của domain khác khi không được cho phép.
- Cors Issue: lỗi việc chia sẻ tài nguyên.
- Fix Cors: cần khai báo Access-Control-Allow-Origin trong Header
- Cors với Nodejs:
    + Sử dụng middleware gắn Access-Control-Allow-Origin vào response.
```js
    app.use(function(req, res, next) {
        res.header("Access-Control-Allow-Origin", "*");
        res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
        next();
    });
```
    + Sử dụng package Cors.
```js
    $ npm install cors
    ...
```

**Authentication/Authorization**
- Authentication (xác thực): xác thưc danh tính của của bạn để cấp quyền khi truy cập vào hệ thống. (name, pass...)
- Các cấp độ của xác thực
    + Single-Factor Authentication: là phương thức đơn giản nhất thường dựa vào mật khẩu.
    + Two-Factor Authentication: xác minh gồm 2 bước. Thường là tên đăng nhập, mật khẩu và 1 private key nào đó chỉ có bạn biết.
    + Multi-Factor Authentication: sử dụng 2 hoặc nhiều mức bảo mật từ các loại xác thực độc lập để cấp quyền. Tất cả yếu tổ phải độc lập để loại bỏ bất kì lỗ hổng nào của hệ thổng.

- Authorization (ủy quyền): quá trình này xảy ra sau khi Authentication thành công.
    + Xác định khả năng truy cập hệ thống của bạn ở mức độ nào để bạn có thể truy cập tài nguyên tương ứng của hệ thống.
    

**JSON web token (JWT)**
- JWT: là một chuẩn mở (RFC 7519) định nghĩa một cách nhỏ gọn và khép kín để truyền một cách an toàn thông tin giữa các bên dưới dạng đối tượng JSON
    + Dùng để truyền thông tin 1 cách an toàn.
    + Có phần chữ ký nên đảm bảo dữ liệu không bị thay đổi khi truyền đi.
- Cấu trúc: có 3 thành phần
    + HEADER:
        . "alg": thuật toán dùng để mã hóa (HMAC SHA256 - HS256 hoặc RSA).)
        . "typ": loại token (mặc định JWT)
    + PAYLOAD:
        . chứa các claims - các biểu thức về thực thể (ví dụ user). 3 loại claims.
        . Reserved claims: là 1 số metadata được định nghĩa trước, 1 số là metadata bắt buộc, số còn lại tuân theo JWT để hợp lệ.
        . Public Claims: biểu thức về thực thể
        . Private Claims: tự định nghĩa và ko trùng 2 claims trên. Tạo ra để chia sẻ thông tin giữa 2 parties đã thỏa thuận và thống nhất trước đó.
    + VERIFY SIGNATURE: chữ ký là chuỗi được mã hóa bới header và payload.

**RESTful API vs GraphQL concept**
- RESTful API:
    + REST (Representational State Transfer): một dạng chuyển đổi cấu trúc dữ liệu, một kiểu kiến trúc để viết API.
    + API - Application Programming Interface (giao diện lập trình ứng dụng): là các phương thức, giao thức kết nối tới các các thư viện, ứng dụng khác.
    => RESTful API: là một tiêu chuẩn dùng trong việc thiết kế API cho các ứng dụng web để tiện cho việc quản lý các resource.
    + Hoạt động chủ yếu dựa vào giao thức HTTP. Các hoạt động sẽ sử dụng những phương thức HTTP riêng.
        . GET (SELECT): Trả về một Resource hoặc một danh sách Resource.
        . POST (CREATE): Tạo mới một Resource.
        . PUT (UPDATE): Cập nhật thông tin cho Resource.
        . DELETE (DELETE): Xoá một Resource.
- GraphQL: là một tiêu chuẩn API mới cung cấp một giải pháp hiệu quả, mạnh mẽ và linh hoạt hơn thay thế cho REST.
    + Cho phép client có thể xác định chính xác dữ liệu cần lấy về từ server.

**POSTMAN**
- Postman là 1 ứng dụng REST Client, dùng để thực hiện test, gửi các request, API mà không cần sử dụng browser.

**Web Application**
- Web Application (Web App):
    + Web (Website): tập hợp nhiều trang web đơn lẻ thành 1 trang web lớn có chung tên miền là website.
    + App (Application): là một loại chương trình có khả năng làm cho máy tính thực hiện trực tiếp một công việc nào đó người dùng muốn thực hiện.
    => Web App: những ứng dụng chạy trên web. Thông qua web app người sử dụng có thể một số công việc như tính toán, chia sẻ, mua sắm.
- Cấu tạo:
    + Trình duyệt web.
    + Server
    + Cơ sở dữ liệu.
- Cách thức hoạt động.
    + Khi người sử dụng trình duyệt sẽ gửi yêu cầu. Khi nhận được yêu cầu, tại đây server sẽ tạo ra truy vấn và cập nhật cơ sở dữ liệu và tạo ra giao diện người dùng.\
- Khi người dùng gõ 1 địa chỉ web site lên thanh address bar của trình duyệt:
    + Máy tính sẽ đọc file host trong máy để xem địa chị bạn gõ xem domain tương ướng với ip nào.
    + Nếu không có, trình duyệt kiểm tra trong DNS (Domain Name Server - server chứa toàn bộ domain name) để lấy ip tương ứng.
    + Khi clinet đã có được ip tương ứng, sẽ kết nối tới server thông qua giao thức TCP (giao thức truyền thông tin qua lại giữ client - server).
    + Kết nối thành công, client sẽ truyền HTTP với phương thức GET với url.
    + Server trả về cho client HTML. Client đọc file HTML thấy có thêm file như css, js sẽ yêu cầu server gửi cho 2 file trên và render ra giao diện cho người dùng.