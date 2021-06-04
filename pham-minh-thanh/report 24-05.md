# **_Nodejs core modules_**

File system
- Module này để tương tác với các file như dạng pdf, doc, html ...
  var http = require('http');
  var fs = require('fs');
  http.createServer(function (req, res) {
    fs.readFile('demofile1.doc', function(err, data) {
      res.writeHead(200, {'Content-Type': 'text/html'});
      res.write(data);
      return res.end();
    });
  }).listen(8080);
OS
- Module này để tương tác với các thành phần trong hệ điều hành
Stream
- Streams là một collections của dữ liệu giống như strings hay arrays, sự khác nhau duy nhất đó là các streams không tồn tại cùng một lúc do đó không cần chiếm nhiều bộ nhớ. Điều khiến streams thực sự mạnh đó là khả năng làm việc khi xử lý với dữ liệu lớn (big data) hay nguồn dữ liệu đến từ nguồn bên ngoài một chút một.
- Streams cho phép bạn đọc dữ liệu từ một nguồn hoặc viết dữ liệu đến một đích đến nào đó. Trong NodeJS, có 4 loại streams khác nhau:

+ Readable: đây là loại streams chỉ dùng để đọc..
+ Writable : đây là loại streams chỉ dùng để ghi..
+ Duplex : sử dụng cả 2 đọc và ghi.
+ Transform : một loại của Duplex nhưng khác nhau bởi kết quả của đầu ra dựa vào đầu vào.

Mỗi streams đều được cấp một EventEmitter cho phép chúng ta bắt sự kiện theo từng thời điểm cụ thể. Sau đây là một vài sự kiên hay dùng :

data: sự kiện này được kích hoạt khi dữ liệu được đọc
end: sự kiện này được kích hoạt khi không còn dữ liệu để đọc
error: sự kiện này được kích hoạt khi xảy ra lỗi.
finish: sự kiện này được kích hoạt khi hoàn thành (dữ liệu đã được đẩy hết về hệ thống cơ sở)

Events (*):
- 
HTTP
- Module giúp truyền dẫn siêu văn bản Hyper Text Transfer Protocol (HTTP)
Create HTTP Server:
  var http = require('http');

  //create a server object:
  http.createServer(function (req, res) {
    res.write('Hello World!'); //write a response to the client
    res.end(); //end the response
  }).listen(8080); //the server object listens on port 8080
Path

Path
- Module được sử dụng để thao tác với đường dẫn của các tập tin


# **_Data analyst_**

Chuẩn hoá (1NF, 2NF, 3NF, BCNF) và phi chuẩn hoá dữ liệu
- Nếu dữ liệu không được chuẩn hóa: 
+ Dư thừa dữ liệu
+ Dữ liệu không nhất quán
+ Khó cập nhật, truy xuất dữ liệu

- Mục đích của việc chuẩn hóa dữ liệu
+ Giảm dư thừa dữ liệu
+ Đảm bảo tính nhất quán của dữ liệu
+ Hỗ trợ dễ dàng cập nhật, truy xuất dữ liệu

Chuẩn 1NF
- Dữ liệu không lặp
- Thuộc tính (colum) không chứa giá trị phức
- Không chứa các thuộc tính có thể tính toán từ các thuộc tính khác
- Xác đinh được trường thuộc tính khóa chính

Chuẩn 2NF
- Nó phải là dạng chuẩn 1
- Các trường thuộc tính không phải là khóa chính, phải phụ thuộc hoàn toàn vào khóa chính. Không được phep phụ thuộc vào 1 phân của khóa chính

Chuẩn 3NF
- Phải là quan hệ đạt dạng chuẩn 2
- Các trường thuộc tính không phải là khóa chính, phải phụ thuộc trực tiếp vào khóa chính. Không được phép phụ thuộc bắc cầu thông qua thuộc tính khác.
