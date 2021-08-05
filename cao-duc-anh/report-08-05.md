**DOM**
    DOM là viết tắt của Document Object Model. HTML DOM là một Object model và Programming interface cho HTML. Với HTML DOM, JS có thể truy cập, thay đổi, thêm, xoá tất cả các element trong một file HTML. 

    Trong DOM, tất cả các Elements đều là các Objects. The Programming interface là các properties và methods của từng Objects.
    A property là một giá trị có thể truy cập, thay đổi.
    A method là một hành động như là thêm hoặc xoá một HTML Element.

**BOM**
    BOM là viết tắt của Browser Object Model. Browser được xem như là một Object - Window. Tất cả các Object, functions, variables là Global thì đều thuộc về Window. Trong dó, global variables chính là properties của object Window và global function là methods của object Window.
```js
    window.document.getElementById("header");
    //tương tự với dòng sau:
    document.getElementById("header");
```

**setTimeout/clearTimeout**
    setTimeout() có thể gọi một function hoặc tính toán biểu thức sau một khoảng thời gian nhất định, tính bằng milliseconds. (1000 ms = 1 second)
    Function sẽ chỉ được thực hiện một lần.
```js
    setTimeout(function() { alert("Hello"); }, 3000);
```
    clearTimeout() dùng để dừng function được gán trong setTimeout() thực thi. Để sử dụng được clearTimeout, khi gọi setTimeout() bắt buộc phải gán vào một variable để có thể sử dụng làm parameter cho lệnh clearTimeout().
```js
    myVar = setTimeout(function() { alert("Hello"); }, 3000);
    clearTimeout(myVar);
```

**setInterval/clearInterval**
    setInverval tương tự như setTimeout, điểm khác ở đây là function sẽ được thực hiện lặp đi lặp lại cho đến khi window bị đóng hoặc lệnh clearInterval được gọi ra.
    Tương tự như clearTimeout, clearInterval dùng để dừng lệnh setInterval và bắt buộc khi khai báo setInterval phải được gán vào một variable để dùng làm parameter cho clearInterval.

**Callback**
    Là một function được truyền vào một function khác như một parameter, sau đó sẽ được thực thi bên trong hàm function đó.

```js
    function alertCallback() {
        alert('Welcome!');
    }
    function logAndAlert(anotherFunction) {
        console.log('User acessed to web');
        anotherFunction();
    }

    logAndAlert(alertCallback);
    //Lúc này sẽ vừa có một pop-up Welcome và console sẽ có User acessed to web.
```

**cookie/localStorage/sessionStorage**
    - LocalStorage và sessionStorage được lưu trữ trên trình duyệt của người dùng. sessionStorage giới hạn trong một cửa sổ hoặc tab của trình duyệt. Một trang web được mở trong hai thẻ của cùng 1 trình duyệt cũng không thể truy xuất dữ liệu của nhau. Như vậy khi đóng trang web thì dữ liệu lưu trong sessionStorage hiện tại cũng bị xoá. Còn localStorage có thể truy xuất lẫn nhau giữa các cửa sổ trình duyệt, dữ liệu được lưu không giới hạn thời gian.
    - localStorage chỉ bị xoá bằng JS hoặc xoá bộ nhớ trình duyệt, hoặc xoá bằng localStorageAPI. Lưu trữ được lên tới 5MB và không gửi thông tin lên server.
    - sessionStorage được cũng được lưu trong trình duyệt của client. Mất dữ liệu khi đóng tab, thông tin được lưu trữ ít nhất là 5MB.

    - Cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính khi truy cập vào trang web, mỗi khi tải trang web, browser sẽ gửi cookie để báo cho trang web các hoạt động trước đó của người dùng. Cookie chủ yếu để đọc phía server, có khoảng thời gian timeout nhất định do lập trình viên xác định trước. Chỉ có thể lưu trữ tối đa 4KB và vài chục cookie cho một domain.
    