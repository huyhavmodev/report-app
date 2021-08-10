# NGUYỄN THÀNH LUÂN - Report 08/10:

**ES6**

**Template String**
- Template String: sử dụng bằng cách dùng cặp dấu ``:
```js
    // Cách thông thường
    var fullName = 'Nguyen Thanh Luan';
    var output = 'My name is: ' + fullName;
    
    // Sử dụng template string
    var fullName = 'Nguyen Thanh Luan';
    var output = `My name is: ${fullName}`;
```

**Destructuring and Rest parameters**
- Destructuring: phân rã.
- Rest parameters: sử dụng dấy 3 chấm (...) lấy ra những phần còn lại
``` js
    // Cách thông thường
    var arr = [1, 2, 3, 4, 5];
    conslog(arr[0]); // Run => 1

    // Sử dụng destructuring
    var arr = [1, 2, 3, 4, 5];
    var [index0, index1, index2] = arr;
    console.log(index0) // Run => 1

    // Destructuring kết hợp rest parameters
    var arr = [1, 2, 3, 4, 5];
    var [index0, index1, index2, ...params] = arr;
    console.log(params); // Run => [4, 5]
```

**Default parameter**
- Default parameter value: giá trị tham số mặc định
    + với những tham số bắt buộc phải nhập vào thì không cần set giá trị mặc định.
    + với những tham số không bắt buộc phải nhập vào thì cần set giá trị mặc định
```js
    function myInfo(fullname)
    {
        console.log(fullname);
    }
    myInfo('Nguyen Thanh Luan');

    // để set giá trị mặc định
    function myInfo(fullname = 'NTL')
    {
        console.log(fullname);
    }
    myInfo();
```

**Spread**
- Cú pháp: giống với rest parameters là dùng dấu 3 chấm (...)
- Ví dụ dưới thì spread sẽ bỏ cặp ngoặc vuông và lấy tất cả giá trị bên trong.
```js
    var arr1 = [1,2,3];
    var arr2 = [4,5,6];
    var arr3 = [...arr1,...arr2];
    console.log(arr3); // Run => [1,2,3,4,5,6]
```

**NodeJS and NPM**
- NodeJS: là một nền tảng (Platform) phát triển độc lập được xây dựng ở trên Javascript Runtime của Chrome mà chúng ta có thể xây dựng được các ứng dụng mạng một cách nhanh chóng và dễ dàng mở rộng.
    + Phần Core bên dưới của Nodejs được viết hầu hết bằng C++ nên cho tốc độ xử lý và hiệu năng khá cao.
    + Nodejs tạo ra được các ứng dụng có tốc độ xử lý nhanh, realtime thời gian thực.
    + Nodejs áp dụng cho các sản phẩm có lượng truy cập lớn, cần mở rộng nhanh, cần đổi mới công nghệ, hoặc tạo ra các dự án Startup nhanh nhất có thể.
- NPM - Node Package Manager: phần mềm quản lý và phân phối các gói (package) dành cho Node.

***What's LTS (Long-term support)?**
- NodeJS LTS: là phiên bản chú trọng vào tính ổn định (stability), bảo mật (security) và tuổi thọ (lifespan). Khi một phiên bản Node.js được đưa vào LTS thì đồng nghĩa với việc sẽ không có một tính năng mới nào được cập nhật ở phiên bản đó. Thay vào đó sẽ là những thay đổi trong sửa lỗi, cập nhật bảo mật, cập nhật phiên bản npm và cải thiện hiệu năng (performance). 
- NodeJS Stable chú trọng vào cập nhật tính năng và những thay đổi mới nhất. Phiên bản này sẽ được cập nhật khoảng 2 tuần đến 1 tháng một lần. Lưu ý là phiên bản này mặc dù chú trọng cập nhật nhưng vẫn là một phiên bản Stable, không phải Beta. Do đó mức độ ổn định là đủ cho mục đích sử dụng thông thường.

**Dependencies vs devDependencies vs peerDependencies**
- Dependencies: những module được dùng trong quá trình chạy sản phẩm thực tế.
- devDependencies: những module chỉ được dùng vào mục đích phát triển sản phẩm.
    + để chuyển từ Dependencies -> devDependencies: thêm --save-dev vào sau câu lệnh cài đặt package
- peerDependencies: 
    ├── request@2.12.0
    └─┬ some-other-library@1.2.3
      └── request@1.9.9

**package-lock.json and yarn.lock**
- package-lock.json: là file được tạo ra tự động khi sử dụng npm từ  bản ^5.x.x
    + Trong package-lock.json sẽ chỉ định rõ phiên bản, location, mã băm toàn vẹn integrity cho mỗi module và từng dependencies của nó.
    => Cài đặt của nó tạo ra sẽ luôn giống nhau cho dù bạn cài đặt vào lúc nào.
- yarn.lock: Yarn xác định chính xác duy nhất một version mà bạn đã cài vào file yarn.lock.
    + Các máy khác khi cài đặt dependencies sẽ tự động dựa vào yarn.lock để cài lại chính xác version của module mà bạn đã cài trên máy bạn đồng thời vẫn cho phép cài đặt module với range xác định trong package.json.
**API**
- API - Application Programming Interface (giao diện lập trình ứng dụng): là các phương thức, giao thức kết nối tới các các thư viện, ứng dụng khác.
- WEB API: là một phương thức dùng để cho phép các ứng dụng khác nhau có thể giao tiếp, trao đổi dữ liệu qua lại.
    + Dữ liệu được Web API trả lại thường ở dạng JSON hoặc XML thông qua giao thức HTTP hoặc HTTPS.

**HTTP Request (OPTIONS, GET, POST, PUT, PATH, DELETE)**
- HTTP: HyperText Transfer Protocol: giao thức truyền tải siêu văn bản.
    + OPTIONS: trả về phương thức HTTP mà server hỗ trợ.
    + GET: phương thức này dùng để lấy thông tin từ server sử dụng URI. Và phương thức GET chỉ nên dùng để lấy thông tin mà không có ảnh hưởng khác tới dữ liệu.
    + POST: phương thức này dùng để gửi dữ liệu từ client lên server, ví dụ: thông tin khách hàng, file,...
    + PUT: dùng để thay thế dữ liệu hiện tại trên server bằng một dữ liệu mới được tải lên (upload dữ liệu).
    + DELETE: xóa một tài nguyên định trước.
- HTTP Status Codes
    + 1xx: information Message
        Các status code này chỉ có tính chất tạm thời, client có thể không quan tâm.
    + 2xx Successful
        Khi đã xử lý thành công request của client, server trả về status dạng này:
        . 200 OK: request thành công.
        . 202 Accepted: request đã được nhận, nhưng không có kết quả nào trả về, thông báo cho client tiếp tục chờ đợi.
        . 204 No Content: request đã được xử lý nhưng không có thành phần nào được trả về.
        . 205 Reset: giống như 204 nhưng mã này còn yêu câu client reset lại document view.
        . 206 Partial Content: server chỉ gửi về một phần dữ liệu, phụ thuộc vào giá trị range header của client đã gửi.
    + 3xx Redirection
        Server thông báo cho client phải thực hiện thêm thao tác để hoàn tất request:
        . 301 Moved Permanently: tài nguyên đã được chuyển hoàn toàn tới địa chỉ Location trong HTTP response.
        . 303 See other: tài nguyên đã được chuyển tạm thời tới địa chỉ Location trong HTTP response.
        . 304 Not Modified: tài nguyên không thay đổi từ lần cuối client request, nên client có thể sử dụng đã lưu trong cache.
    + 4xx Client error
        Lỗi của client:
        . 400 Bad Request: request không đúng dạng, cú pháp.
        . 401 Unauthorized: client chưa xác thực.
        . 403 Forbidden: client không có quyền truy cập.
        . 404 Not Found: không tìm thấy tài nguyên.
        . 405 Method Not Allowed: phương thức không được server hỗ trợ.
    + 5xx Server Error
        Lỗi của server:
        . 500 Internal Server Error: có lỗi trong quá trình xử lý của server.
        . 501 Not Implemented: server không hỗ trợ chức năng client yêu cầu.
        . 503 Service Unavailable: Server bị quá tải, hoặc bị lỗi xử lý.