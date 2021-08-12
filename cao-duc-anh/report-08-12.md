**Web Application**

- Web Application (Web App):

  - Web (Website): tập hợp nhiều trang web đơn lẻ thành 1 trang web lớn có chung tên miền là website.
  - App (Application): web app là những ứng dụng chạy trên web. Thông qua web app, người dùng có thể thực hiện một số công việc: tính toán, chia sẻ hình ảnh, mua sắm … Tính tương tác của web app cao hơn website rất nhiều.

- Cấu tạo:
  Một ứng dụng Web thông thường được cáu trúc như một ứng dụng ba lớp.
  - Trình duyệt web là lớp thứ nhất
  - Server sử dụng các các công nghệ cung cấp web động là lớp thứ 2
  - Database là lớp thứ 3
- Cách thức hoạt động.
  - Khi người sử dụng trình duyệt sẽ gửi yêu cầu. Khi nhận được yêu cầu, tại đây server sẽ tạo ra truy vấn và cập nhật cơ sở dữ liệu và tạo ra giao diện người dùng.\
- Khi người dùng gõ 1 địa chỉ web site lên thanh address bar của trình duyệt:
  - Máy tính sẽ đọc file host trong máy để xem URL bạn gõ xem domain tương ướng với IP nào.
  - Nếu không có, trình duyệt kiểm tra trong DNS (Domain Name Server - server chứa toàn bộ domain name) để lấy IP tương ứng.
  - Khi client đã có được IP tương ứng, sẽ kết nối tới server thông qua Protocol.
  - Client sẽ gửi Request cho server.
  - Server sẽ chạy phần mềm web server để chấp nhận các Request, sau đó Web application sẽ tạo thành trang web động thông qua dữ liệu từ database
  - Server Response cho Browser hiển thị thông qua các file HTML,CSS,JS
