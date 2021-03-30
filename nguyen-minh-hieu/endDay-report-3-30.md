## Nguyen Minh Hieu - 03/30

### Topic: AJAX Là gì?

#### 1. AJAX là gì? 
- AJAX là phương pháp trao đổi dữ liệu dữ với server và cập nhật 1 hay nhiều phần của trang web mà không phải reload lại toàn bộ trang.
- AJAX được viết bằng javascript và chạy trên client

#### 2. Tại sao lại sử dụng AJAX?
- giúp tăng trải nghiệm người dùng, khi cần thay đổi gì đó không phải load lại cả trang.
- được dùng để thực hiện lưu trữ và truy xuất dữ liệu mà k load lại trang tiết kiệm băng thông, giảm thiểu tốc độ tải trang.

#### 3. cách thức hoạt động 
1. từ trình duyệt của client, ta gọi 1 even để gọi ajax. Khi đó js tạo 1 đối tượng XMLHttpRequest sau đó đối tượng này gửi 1 request đến server.
2. Khi server nhận đc HttpRequest, xử lý request và trả về response.

3. Sau khi nhận đc response từ server, Javascript sẽ xử lý và cập nhật vào trang web.

ví dụ đơn giản sử dụng ajax bằng jQuery: 
``` javascript
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.14.4/jquery.min.js"></script>
<script>
$(document).ready(function(){
    $("button").click(function(){
        $("#div-1").load("demo.html");
    });
});
</script>
</head>
<body>

<div id="div-1"><h2>Let jQuery AJAX Change This Text</h2></div>

<button>Get External Content</button>

</body>
</html>
```