# Nguyễn Huy An

## CORS
- CORS là một cơ chế cho phép nhiều tài nguyên khác nhau (fonts, Javascript, v.v…) của một trang web có thể được truy vấn từ domain khác với domain của trang đó. CORS là viết tắt của từ Cross-origin resource sharing.
- Khi call API tới server mà không có header Access-Control-Allow-Origin hoặc giá trị của nó không hợp lệ thì sẽ phát sinh lỗi này và không lấy được dữ liệu từ API. Cách khắc phục lỗi trên là phải config enable CORS lên để phía client có thể gọi được dữ liệu.
- CORS được sinh ra là vì same-origin policy, là một chính sách liên quan đến bảo mật được cài đặt vào toàn bộ các trình duyệt hiện nay. Chính sách này ngăn chặn việc truy cập tài nguyên của các domain khác một cách vô tội vạ.

### Ví dụ
- Khi truy cập vào trang web có mã độc mà trang đó sử dụng JS để truy cập tin nhắn FB ở 1 địa chỉ nào đó. Nếu đã đăng nhập FB từ trước rồi mà k có same-origin policy thì web độc có thể thoải mái lấy hết dữ liệu

```javascript
const createCORSRequest = (method, url) => {
    let xhr = new XMLHttpRequest();
    if ('withCredentials' in xhr) {
        // Kiểm tra XMLHttpRequest object có thuộc tính
		// withCredentials hay không
        // Thuộc tính này chỉ có ở XMLHttpRequest2
        xhr.open(method, url, true);
    } else if (typeof XDomainRequest != 'undefined') {
        // Kiểm tra XDomainRequest
        // Đây là đối tượng chỉ có ở IE và
		// là cách để IE thực hiện truy vấn CORS
        xhr = new XDomainRequest();
        xhr.open(method, url);
    } else {
        xhr = null;
    }
    return xhr;
}

const request = createCORSRequest('GET', 
	'https://jsonplaceholder.typicode.com/posts/1');
if (!request) {
    throw new Error('CORS is not supported');
}
```
- Theo nguồn em đọc thì CORS thường sẽ do backend xử lí

### withCredentials
- các truy vấn CORS không gửi hoặc thiết lập bất cứ cookie nào trên trình duyệt. Nếu muốn sử dụng cookie trong truy vấn đó, chúng ta phải đặt thuộc tính withCredentials của truy vấn bằng true
### Send request
- Sau khi đã hoàn tất thì sẽ gửi request (request.send()). Lúc này truy vấn sẽ được gửi đến máy chủ, và nếu máy chủ đó chấp nhận CORS thì nó sẽ trả về response tương ứng

## API là gì
- Application Programming Interface cung cấp khả năng truy xuất đến 1 tập các hàm hay dùng, từ đó trao đổi dữ liệu giữa các ứng dụng

### Đặc điểm
- Sử dụng mã nguồn mở
- Đáp ứng đủ thành phần HTTP
- Mô hình web API dùng để hỗ trợ MVC

## HTTP request
- Cấu trúc: 
<method> <request-URL> <http-serverion>
<headers>
<body>

### Các method:
- GET, POST.. ngoài ra còn có 1 số phương thức khác

### URL
- URL là địa chỉ định danh tài nguyên. Hiểu đơn giản, URL là đường dẫn.  Trong trường hợp Request không yêu cầu tài nguyên cụ thể , URI có thể là dấu *.

### HTTP version
- HTTP version là Phiên bản HTTP đang sử dụng.

