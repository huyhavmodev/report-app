# AJAX

- AJAX viết tắt của Asynchoronus JavaScript And XML, xử lý bất đồng bộ js và XML, là một kỹ thuật bất đồng bộ để lấy dữ liệu từ server mà không phải tải lại toàn bộ trang web.
- Tuy viết tắt X là XML nhưng hiện nay AJAX có thể sử dụng JSON để thay thế cho XML bởi tính gọn nhẹ và tích hợp với JS và ngoài ra nó cũng có thể nhận về một file HTML hoặc một file text.
- Kỹ thuật này bao gồm việc:
  - Gửi yêu cầu lên server mà không phải tải lại trang.
  - Nhận và xử lý dữ liệu mà server gửi về.

## 1. Gửi yêu cầu lên server:

- Để tạo req, ta cần dùng instance của object với các phương thức cần thiết, ở đây ta dùng XMLHttpRequest object, với các trình duyệt cũ, như IE thì dùng ActiveXObject:
  ```javascript
  if (window.XMLHttpRequest) {
    // Mozilla, Safari, IE7+ ...
    httpRequest = new XMLHttpRequest();
  } else if (window.ActiveXObject) {
    // IE 6 and older
    httpRequest = new ActiveXObject("Microsoft.XMLHTTP");
  }
  ```
- Sau đó ta cần tham chiếu cho thuộc tính `onreadystatechange` của đối tượng `XMLHttpRequest` rằng `function` nào sẽ xử lý res trả về, syntax:
  ```javascript
  httpRequest.onreadystatechange = functionName;
  // hoặc
  httpRequest.onreadystatechange = function () {
    //do something
  };
  ```
- Sau khi khai báo như trên ta có thể bắt đầu gọi một req lên server bằng `open()` và `send()`, syntax:

  ```javascript
  httpRequest.open("GET", "http://www.example.org/some.file", true);

  httpRequest.send();
  ```

  - Với `"GET"` là phương thức _HTTP req_ - `GET`, `POST`, `HEAD` và phải viết hoa nếu không một số trình duyệt có thể sẽ không gửi req vì không nhận dạng được kiểu _req_
  - Còn `"http://www.example.org/some.file"` là đường dẫn _URL_ mà ta gửi _req_ tới và chỉ được giới hạn tại domain hiện tại của trang web, không gửi req được tới domain của bên thứ 3.
  - Còn tham số cuối cùng (tùy chọn) để XMLHttpRequest biết được _req_ ở đây có phải bất đồng bộ hay ko, mặc định là `true` nếu ta ko khai báo gì
  - Sau đó, gọi hàm `send()`, nếu có bất kỳ data nào cần gửi lên thì ta sẽ truyền tham số vào cho `send()`
    - Nhưng với `GET` chỉ nên dùng để lấy giá trị chứ không gửi dữ liệu lên server do tính bảo mật, đối với những thông tin quan trọng như username, password.
    - Với dữ liệu được gửi lên server qua `POST` thì dữ liệu phải viết theo format mà server có thể phân tích,
      ```javascript
      "name=value&anothername=" + encodeURIComponent(myVar) + "&so=on";
      ```

## 2. Xử lý dữ liệu server gửi về:

- Nhớ rằng ta đã khai báo `function` xử lý res, nhưng cụ thể thì `function` này sẽ làm gì.
- Đầu tiên cần phải check xem server status bằng giá trị của `httpRequest.readyState` nếu nó bằng giá trị của `httpRequest.DONE` thì res của server đã được trả về và ta có thể xử lý dữ liệu đó.

  ```javascript
  if (httpRequest.readyState === XMLHttpRequest.DONE) {
    // Everything is good, the response was received.
  } else {
    // Not ready yet.
  }
  ```

  - `httpRequest.readyState` có 5 giá trị:

  | Value | State            | Description                                                   |
  | ----- | ---------------- | ------------------------------------------------------------- |
  | 0     | UNSENT           | Client has been created. open() not called yet.               |
  | 1     | OPENED           | open() has been called.                                       |
  | 2     | HEADERS_RECEIVED | send() has been called, and headers and status are available. |
  | 3     | LOADING          | Downloading; responseText holds partial data.                 |
  | 4     | DONE             | The operation is complete.                                    |

- Tiếp theo, check response status code của res:
  ```javascript
  if (httpRequest.status === 200) {
    // Perfect!
  } else {
    // There was a problem with the request.
    // For example, the response may have a 404 (Not Found)
    // or 500 (Internal Server Error) response code.
  }
  ```
  - Những code có thể là :
    | Value | State |
    | ----- | ---------------- |
    | 100-199 | Informational responses |
    | 200-299 | Successful responses |
    | 300-399 | Redirects |
    | 400-499 | Client errors |
    | 500-599 | Server errors |
- Sau khi `state` và `status code` của res đều `OK` hết ta có thế bắt đầu xử lý dữ liệu đã được gửi về, truy cập dữ liệu với 2 phương thức:
  - `httpRequest.responseText` - trả về dữ liệu dưới dạng 1 chuỗi hoặc file text
  - `httpRequest.responseXML` - trả về dữ liệu dưới dạng tài liệu XML, ta có thể xử lý bằng các phương thức của JS DOM.
