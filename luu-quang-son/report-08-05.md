**DOM - Document Object Model**
    -- DOM (mô hình đối tượng tài liệu) là một programming interface cho các tài liệu HTML và XML. Nó đại diện cho trang để các chương trình có thể thay đổi cấu trúc document, style và nội dung. DOM mô tả document dưới dạng các nodes và objects. Bằng cách đó, ngôn ngữ lập trình có thể kết nối với trang.

**BOM**

    -- BOM là chữ viết tắt của Browser Object Model, hay còn gọi là các đối tượng liên quan đến trình duyệt browser. Mỗi browser sẽ có những đối tượng khác nhau nên nó không có một chuẩn chung nào cả
    -- Các loại BOM : 
        -window
        -screen
        -location
        -history
        -navigator
        -popup
        -timing
        -cookies

**CALLBACK**
    -- Là 1 hàm và được truyền qua đổi số bởi 1 hàm khác.
```js
    function myName(param){
        console.log(typeof param);
    }
    function myCallback(value){
        console.log('value', value);
    }
    myName(myCallback); ///function
```

**Array**
    --Array, hay được gọi là mảng, là kiểu dữ liệu mà giá trị của nó chứa nhiều giá trị khác. Mỗi giá trị của mảng được gọi là element (phần tử).
    -- Có 2 cách khai báo 1 array
```js
        var foo = [];
        var number = [1, 2, 3, 4, 5];
// hoặc
        var foo = new Array()
        var number = new Array(1, 2, 3, 4, 5);
```

    -- Thuộc tính length đưa ra độ dài của mảng.
    -- Các phương thức trong Array: 

        1. Array.prototype.push() -- Phương thức thêm một phần tử vào cuối mảng và trả về độ dài của mảng.
```js
        const number = [1, 2, 3];
        number.push(5); // 4
        console.log(number) // [1, 2, 3, 5]
```

        2. Array.prototype.pop() -- Phương thức xóa phần tử cuối của mảng và trả về phần tử đã xóa.

```js
        const number = [1, 2, 3];
        number.pop(); // 3
        console.log(number); // [1, 2]
``` 
        3. Array.prototype.shift() -- Giống như pop, phương thức này xóa phần tử đầu tiên của mảng và trả về phần tử đó.
```js
        const number = [1, 2, 3];
        number.shift(); // 1
        console.log(number); // [2, 3]
```
        4. Array.prototype.filter() -- Lặp các phần tử trong mảng đã cho và trả về một mảng mới với các phần tử thõa mãn điều kiện lọc. Ví dụ dưới đây dùng 'arrow function' :
```js
        var numbers = [1, 34, 5, 2, 67, 46, 24];
        number.filter(number => number % 2 === 0)
        // [34, 2, 46, 24]
```

        5. Array.prototype.map() -- Tạo một mảng mới với sự biến đổi của các phần tử trong mảng.
```js
        var numbers = [1, 2, 3, 4, 5];
        number.map(number => number * 2)
        // [2, 4, 6, 8, 10]
```
        6. Array.prototype.find() -- Trả về một phần tử đầu tiên trong mảng thõa mãn điều kiện tìm kiếm.
```js
        var days = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday'];
        days.find(day => day.length === 6)
        // 'Sunday'
```
        7. Array.prototype.reduce() duyệt qua các phần tử trong mảng và gọi một callback trên mỗi phần tử, các giá trị trả về sẽ truyền từ callback này sang callback khác, cuối cùng trả về giá trị sau khi duyệt đến cuối mảng.
```js
        var frui = [
    { name: 'apple', price: 10 },
    { name: 'orange', price: 50 },
    { name: 'tomato', price: 150 }, 
    { name: 'coconut', price: 80 },
    { name: 'pear', price: 200 },
    ];

    frui.reduce((total, item) => {
        if (item.price > 50) {
            return total + item.price;
        }
        return total;
    }, 0)
```


**Multidimensional Arrays**
```js   
            
	var 2D_array = [
					[item1, item2, item3],
					[item4, item5, item6],
					...
					]

```

**Access and Iterate Through an Array**
**Bubbling and capturing**
**Bubbling** Khi 1 event xảy ra trong một element, Nó sẽ chạy handler của nó, tiếp theo là thằng cha, rồi tới những thằng trên thằng cha

**capturing**
Reference : https://viblo.asia/p/bubbling-and-capturing-gDVK2erm5Lj


**Regular-expressions**
    -- có 2 cách để khởi tạo 1 Regex 
```js
        var re1 = new RegExp("abc"); // sử dụng hàm khởi tạo
        var re2 = /abc/;    // sử dụng cặp //
```