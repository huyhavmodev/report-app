# NGUYỄN THÀNH LUÂN - Report 08/02:

# Day 3.

* this, apply, call, bind
* setTimeout/clearTimeout
* setInterval/clearInterval
* requestAnimationFrame/cancelAnimationFrame
* cookie/localStorage/sessionStorage
* DOM - Document Object Model
* BOM - Browser Object Model
* Callback


**this, apply, call, bind**
- This: đề cập đến đối tượng mà nó thuộc về.
    + Khi đứng 1 mình: this đề cập đến đối tượng global (window).
    + this trong hàm tạo đại diện cho đối tượng sẽ được tạo.
    + Trong phương thức: this tham chiếu tới đối tượng truy cập phương thức ( đối tượng trước dấu ".")
    + this trong 1 hàm là undefined khi ở chế độ 'strict mode'.

```js
    console.log(this) // window

    var myInfo = {
        firstName: 'Luan',
        lastName: 'Nguyen',
        fullName(){
            console.log(this);
        },

        myInfoChild: {
            name: 'My Info1',
            methodChild(){
                console.log(this);
            }
        }
    }
    console.log(myInfo.fullName());
     // this ở đây thuộc đại diện cho đối tượng myInfo
     // Run => Luan Nguyen

    console.log(myInfo.myInfoChild.methodChild());
    // this ở đây tham chiếu tới đối tượng truy cập phương thức trươc dấu chấm
    // Run => object myInfoChild
```
- Apply và Call: đều là phương thức bạn có thể sử dụng trên các đối tượng khác nhau.
    + Apply: lấy đối số theo mảng
    + Call: lấy đối số riêng biệt

```js
    // Apply
    const person = {
    fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
        }
    }
    const person1 = {
        firstName:"Luan",
        lastName: "Nguyen"
    }
    console.log(person.fullName.apply(person1, ["Ha Noi", "Viet Nam"]));

    // Call
    const person = {
    fullName: function(city, country) {
        return this.firstName + " " + this.lastName + "," + city + "," + country;
        }
    }
    const person1 = {
        firstName:"Luan",
        lastName: "Nguyen"
    }
    console.log(person.fullName.call(person1, "Ha Noi", "Viet Nam"));
```

- Bind: hàm này sẽ trả về 1 hàm mới, có thể nhận các đối số như hàm ban đầu. Cho phép rằng buộc 'this' cho 1 phương thức

```js
    this.firstName = 'Luong';
    this.lastName = 'Tho';
    var myInfo = {
        firstName: 'Luan',
        lastName: 'Nguyen',
        fullName(){
            return this.firstName + " " + this.lastName;
        }
    }
    console.log(myInfo.fullName);
    // Run => Luan Nguyen
    var person = myInfo.fullName;
    console.log(person());
    // Run => Luong Tho
    // từ khóa this ở đây đã trỏ firstName và lastName ở global
    var person1 = myInfo.fullName.bind(myInfo);
    console.log(person1());
    // Run => Luan Nguyen
    // bind: đã ràng buộc từ khóa this theo đối tượng myInfo
```

**setTimeout/clearTimeout**
- setTimeout: là phương thức bất đồng bộ gọi 1 hàm hoặc đánh giá biểu thức sau số mili giây được chỉ định
- clearTimeout: là phương thức xóa 1 bộ hẹn giờ
    + Giá trị ID được trả về bới setTimeout() được sử dụng làm tham số cho clearTimeout()
    + Nếu hàm chưa được thực thi thì sẽ dừng bằng cách gọi clearTimeout()
```js

    console.log(1);
    console.log(2);
    setTimeout(function(){
        console.log(3);
    },5000);
    console.log(4);
    // Run => 1 -> 2 -> 4 -> 3
    // 5000: là số mili giây = 5s

    var process = setTimeout(function(){
        console.log(5);
    },5000);
    clearTimeout(process);  // process sẽ hủy và dừng ngay


```

**setInterval/clearInterval**
- setInterval: là phương thức bất đồng bộ, phương thức gọi 1 hàm hoặc đánh giá biểu thức sau khoảng thời gian nhất định
- - clearInterval: là phương thức để xóa bộ hẹn giờ
```js
    setInterval(function(){
        console.log("Hello");
    },2000);
    // Cứ sau 2s dòng chữ "Hello" lại được in ra và không bao giờ dừng
    
    var process = setInterval(function(){
        console.log("Hi");
    },2000);
    clearInterval(process);
    // clearInterval sẽ xóa tiến trình luôn và chương trình dừng ngay lập tức
```

***cookie/localStorage/sessionStorage**
- Cookie: dữ liệu lưu trong file text, nằm trên máy tính
```js
    document.cooke = "username=luannt";
     // tạo cookie

    document.cookie = "username=luannt; expires=Thu, 04 Aug 2020 12:00:00 UTC";
     // set cookie hết hạn bằng cách set expires bằng 1 ngày đã qua

    document.cookie = "uusername=luannt; expires=Thu, 04 Aug 2020 12:00:00 UTC; path=/";
     // thêm path để biết cookie thuộc đường dẫn nào
```

- localStorage và sessionStorage: đều lưu dữ liệu trên trình duyệt
    + localStorage: dữ liệu được lưu vô thời hạn trừ khi bạn xóa lịch sử, hoặc api.
    + sessionStorage: dữ liệu được lưu có thời hạn và mất đi khi đóng trình duyệt.

**DOM - Document Object Model**
- Với HTML DOM, Javascript có thể truy cập và thay đổi tất cả phần tử của tài liệu HTML.
- HTML DOM (Document Object Model): Là mô hình các đối tượng trong tài liệu HTML:
    + Các phần tử dưới dạng đối tượng.
    + Các thuộc tính của tất cả phần tử HTML.
    + Các phương thưc để truy cập tất cả phần tử HTML.
    + Các sự kiện cho tất cả phần tử HTML.
- Các loại DOM trong Javascript:
    + DOM document: có nhiệm vụ lưu trữ toàn bộ các thành phần trong tài liệu của website
    + DOM element: có nhiệm vụ truy xuất tới thẻ HTML nào đó thông qua các thuộc tính như tên class, id, name của thẻ HTML
    + DOM HTML: có nhiệm vụ thay đổi giá trị nội dung và giá trị thuộc tính của các thẻ HTML
    + DOM CSS: có nhiệm vụ thay đổi các định dạng CSS của thẻ HTML
    + DOM Event: có nhiệm vụ gán các sự kiện như onclick(), onload() vào các thẻ HTML
    + DOM Listener: có nhiệm vụ lắng nghe các sự kiện tác động lên thẻ HTML đó
    + DOM Navigation dùng để quản lý, thao tác với các thẻ HTML, thể hiện mối quan hệ cha - con của các thẻ HTML
    + DOM Node, Nodelist: có nhiệm vụ thao tác với HTML thông qua đối tượng (Object)

```js
    document.getElementById("main__content").innerHTML = "Nguyen Thanh Luan"
    // tìm thẻ có id="main__content" và gán nội dung HTML bên trong là "Nguyen Thanh Luan"
```

**BOM - Browser Object Model**
- BOM - Browser Object Model: là các đối tượng liên quan đến trình duyệt. 
- Các loại BOM:
    + window: đối tượng toàn cục, cấp cao nhất trong BOM.
    + screen: lấy thông tin về màn hình trình duyệt.
    + location: điều hướng url.
    + history: quản lý lịch sử lướt web.
    + navigator: giúp lấy thông tin về trình duyệt mà người dùng đang sử dụng.
    + popup: alert(), confirm(), prompt()
    + timing: setTimeout(), setInterval().
    + cookies: quản lý dữ liệu mà trình duyệt web đã lưu.
    // Các đối tượng trên có phân cấp lẫn nhau và window là lớn nhất
    // Mỗi 1 đối tượng sẽ có các thuộc tính và phương thức riêng