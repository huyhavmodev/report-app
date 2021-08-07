# NGUYỄN THÀNH LUÂN - Report 08/06:

# Day 5.

**Bubbling and capturing**
- Bubbling: Khi một sự kiện xảy ra trên một phần tử, trước tiên nó chạy các trình xử lý trên nó, sau đó đến các trình xử bao lấy nó.
- Capturing: ngược lại với Bubbling, nó sẽ xử lý từ phần tử to nhất đến phần tử bé nhé
```js
    <div>
        <ul>
            <li></li>
        </ul>
    </div>
```
- Trong ví dụ trên:
    + Bubbling: khi có sự kiện, sẽ xử lý từ <li> -> <ul> -> <div>.
    + Capturing: khi có sự kiện, sẽ xử lý từ <div> -> <ul> -> <li>.
- Để ngừng Bubbling: event.stopPropagation()

**Regular-expressions**
- RegEx (regular expression) là tập hợp những quy tắc, dựa vào những quy tắc này ta sẽ viết ra những biểu thức so khớp giữa các chuỗi với nhau.
```js
    /pattern/modifiers
```
- pattern là chuỗi Regular Expression
- modifiers là thông số cấu hình cho chuỗi pattern, và nó có các giá trị sau:
    + i : so khớp không quan tâm đến chữ hoa chữ thường
    + g : so khợp toàn bộ chuỗi cần tìm
    + m : so khớp luôn cả các dữ liệu xuống dòng (multiline)
```js
    var re1 = new RegExp("abc");
    var re2 = /abc/;
    // tạo RegEx biễu diễn 1 chuối có dạng 'abc'.
```

***8 cấu trúc dữ liệu thường dùng**
- Array (mảng).
- Linked list (danh sách liên kết).
- Queue (hàng đợi).
- Stack (ngăn xếp).
- Hash table (bảng băm).
- Set
- Tree (cây).
- Graph (đồ thị).