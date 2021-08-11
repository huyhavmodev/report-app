**AJAX and JSON**
4 điểm chính của AJAX là: + Tạo một object XMLHttpRequest + Khai báo một function callback + Mở, lấy dữ liệu của object XMLHttpRequest

    VỚi AJAX, lập trình viên có thể đọc dữ liệu từ web server sau khi page được load. Update nội dung của web page mà không cần reload cả page. Gửi dữ liệu trở về web server trong background.

    AJAX không phải là một ngôn ngữ lập trình, nó là sự kết hợp của:
    + XMLHttpRequest của browers(Để request dữ liệu từ server)
    + JS và HTML DOM(Để hiển thị hoặc sử dụng dữ liệu)

    Cách thức AJAX hoạt động:
    1. Một event xảy ra trên trang web(vd: Khi trang web load xong, khi một button được click)
    2. Một XMLHttpRequest object được tạo ra bởi JS
    3. XMLHttpRequest object gửi request tpứo server
    4. Server xử lý request
    5. Server gửi response trở lại cho trang web
    6. JS đọc response đó
    7. Hành động phù hợp với dữ liệu trả về được thực thi(VD: update trang web) bới JS

    Tất cả các brower hiện nay đều hỗ trợ và tích hợp sẵn XMLHttpRequest object. Syntax để tạo được một XMLHttpRequest object như sau:

```js
variable = new XHLHttpRequest();
```

    Sau đó là khai báo Callback function để thực thi một đoạn code khi response đã sẵn sàng

```js
xhttp.onload = function () {
  //code
};
```

    SEND a Request: Để gửi một request tới server, ta sử dụng các method của XMLHttpRequest object là: open(), send().

```js
xhttp.open("GET", "ajax_info.txt");
xhttp.send();
```

    JSON là định dạng text để lưu trữ và truyền dữ liệu.

```js
'{"name":"John", "age":30, "car":null}';
```

    JS có thể chuyển đổi từ JSON sang JS object và ngược lại. JSON chỉ là text nên có thể dễ dàng truyền dữ liệu giữa các máy tính và có thể sử dụng bởi bất kỳ ngôn ngữ lập trình nào.
