**API and Authentication concept**

**CORS issue**  là một cơ chế cho phép nhiều tài nguyên khác nhau (fonts, Javascript, v.v…) của một trang web có thể được truy vấn từ domain khác với domain của trang đó
    -- https://viblo.asia/p/cach-khac-phuc-loi-cors-policy-khi-goi-api-tu-frontend-gDVK23aeZLj 

**Authentication/Authorization** sẽ tạo ra một token xác thực, mỗi request người dùng gửi lên đều phải đi kèm với token đó, nếu đúng token thì người dùng mới có thể gọi được tới những api mà chúng ta yêu cầu phải xác thực. Và chúng ta sẽ sử dụng JWT
    
    -- https://viblo.asia/p/authorization-va-authenticate-api-nodejs-voi-jwt-jvEla3exKkw

**JSON web token (JWT)**  một chuẩn mở (RFC 7519) định nghĩa một cách nhỏ gọn và khép kín để truyền một cách an toàn thông tin giữa các bên dưới dạng đối tượng JSON. Thông tin này có thể được xác minh và đáng tin cậy vì nó có chứa chữ ký số. JWTs có thể được ký bằng một thuật toán bí mật (với thuật toán HMAC) hoặc một public / private key sử dụng mã hoá RSA.

    --  Quy trình việc xác thực JWT: 
    1 - Client gửi passWord, nameUser tới server nhằm để xác thực việc đăng nhập

    2 - Nếu login thành công back-end sẽ tạo ra một generate a random String dạng json web token gửi về cho client

    3 - Client nhận token đó, rồi lưu trữ ở đâu đó (cookies, storageSession..)

    4 - Khi client muốn get data gì đó thì luôn gửi kèm token này lên cùng với http request.

    5 - Server nhận được http request từ client thì check token này available hay không? Rồi cho đi tiếp, còn không chặn lại, và có thể report ip này.


**RESTful vs GraphQL concept** tham khảo :
    -- https://viblo.asia/p/so-sanh-graphql-voi-rest-V3m5WLv8KO7

**Postman**  là một công cụ cho phép chúng ta thao tác với API, phổ biến nhất là REST.

    -- Các chức năng cơ bản:
        Cho phép gửi HTTP Request với các method GET, POST, PUT, DELETE.
        Cho phép post dữ liệu dưới dạng form (key-value), text, json.
        Hiện kết quả trả về dạng text, hình ảnh, XML, JSON.
        Hỗ trợ authorization (Oauth1, 2).
        Cho phép thay đổi header của các request.