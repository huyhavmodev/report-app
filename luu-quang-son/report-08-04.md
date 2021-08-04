  # Day3
**this, apply, call, bind**

**call** là gọi hàm và cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy.
```js
        function.call(thisArg, arg1, arg2, ...)
```

**apply** là gọi hàm và cho phép bạn truyền vào một object và các đối số thông qua mảng.
```js
function.apply(thisArg, [argsArray])
```

**Bind** là trả về một hàm số mới, cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy.
```js
var newFunction = fun.bind(thisArg[, arg1[, arg2[, ...]]])
```


**setTimeout/clearTimeout**

**setTimeout** có tác dụng thực thi hành động sau khoảng thời gian nào đó, và nó chỉ thực hiện đúng một lần.
```js
     // setTimeout(function, milliseconds);
      setTimeout(function(){
            alert('Chào mừng bạn đã đến với website toidicode.com');
        },3000);
```

**clearTimeout**  sẽ xóa bộ hẹn giờ bằng phương thức setTimeout() .
```js
        var myVar;
        function myFunction() {
            myVar = setTimeout(function(){ alert("Hello") }, 3000);
    }
        function myStopFunction() {
        clearTimeout(myVar);
    }
```

**setInterval/clearInterval**
    --    Hàm setInterval() sẽ gọi một hàm khác (hoặc một đoạn code) cứ sau một khoảng thời gian ấn định. Hàm này trả về ID của quá trình gọi này. Giá trị ID được dùng để ngắt quá trình gọi lặp lại này bằng hàm clearInterval(ID)

```js
        var i = 0;

    var id = setInterval(myAlert, 3000); //Cứ 3s gọi hàm myAlert một lần

    function myAlert() {
        i++;
        alert("Hi " + i);
        if (i >= 5)
            clearInterval(id);          //Ngắt lặp lại sau 5 lần
    }
```

**requestAnimationFrame/cancelAnimationFrame**
    -- requestAnimationFrame đảm bảo sẽ chạy đoạn code animation ngay trước những lần trình duyệt tiến hành repaint trang web, theo đúng tần số quét của thiết bị (chạy mượt hơn so với setTimeout và setInterval).

**cookie/localStorage/sessionStorage**

**cookie** 
        --  Thông tin được gửi lên server: Cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng, mỗi khi người dùng tải ứng dụng, trình duyệt sẽ gửi cookie để thông báo cho ứng dụng về hoạt động trước đó của bạn. Vì vậy đừng bao giờ lưu trữ những thông tin quan trọng, yêu cầu tính bảo mật cao vào cookie vì nó hoàn toàn có thể bị sửa đổi và đánh cắp, thấp chí có thể lợi dụng điều này để tấn công website của bạn.
        --  Cookie chủ yếu là để đọc phía máy chủ (cũng có thể được đọc ở phía máy khách), localStorage và 
        --  sessionStorage chỉ có thể được đọc ở phía máy khách.
        --  Cookie Có thời gian sống: Mỗi cookie thường có khoảng thời gian timeout nhất định do lập trình viên xác định trước.
        --   Lưu trữ: cho phép lưu trữ tối đa 4KB và vài chục cookie cho một domain.
```js
        1. Tạo cookie: Javascript có thể tạo cookie như sau:
            document.cookie = 'username=Ted Mosby';
        2. Thêm vào ngày hết hạn cho cookie
            document.cookie = 'username=Ted Mosby; expires=Thu, 18 Dec 2018 8:00:00 UTC';
        3. Hoặc đặt hẹn giờ sau bao lâu cookie sẽ hết hạn với max-age (tính bằng giây)

            document.cookie = 'username=Ted Mosby; max-age=9000';
        4.   Đọc cookie:
            var x = document.cookie;
```

**localStorage**
        --Khả năng lưu trữ vô thời hạn: Có nghĩa là chỉ bị xóa bằng JavaScript, hoặc xóa bộ nhớ trình duyệt, hoặc xóa bằng localStorage API.
        --Lưu trữ được 5MB: Local Storage cho phép bạn lưu trữ thông tin tương đối lớn lên đến 5MB, lưu được lượng thông tin lớn nhất trong 3 loại.
        --Không gửi thông tin lên server như Cookie nên bảo mật tốt hơn.
```js
        Khởi tạo localStorage
        localStorage.setItem('key', 'value');
// hoặc
        localStorage.key = 'value';
// hoặc
        localStorage['key'] = 'value';
```

**sessionStorage**
        -- Lưu trên Client: Cũng giống như localStorage thì sessionStorage cũng dùng để lưu trữ dữ liệu trên trình duyệt của khách truy cập (client).
        --Mất dữ liệu khi đóng tab: Dữ liệu của sessionStorage sẽ mất khi bạn đóng trình duyệt.
        --Dữ liệu không được gửi lên Server
        --Thông tin lưu trữ nhiều hơn cookie (ít nhất 5MB)

```js
        if ( typeof(Storage) !== 'undefined') {
    // Khởi tạo sesionStorage
    sessionStorage.setItem('name', 'Ted Mosby');
    // get sessionStorage
    sessionStorage.getItem('name');
    // lấy ra số lượng session đã lưu trữ
    sessionStorage.length;
    // xóa 1 item localStorage
    sessionStorage.removeItem('name');
    // xóa tất cả item trong sesssionStorage
    sessionStorage.clear();
} else {
    alert('Trình duyệt của bạn không hỗ trợ!');
}
```