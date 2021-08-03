**Hoisting**
    Hoisting là việc các khai báo biến hoặc hàm sẽ được chuyển lên trên cùng của scope của nó.
    
    Trình biên dịch của JS có 2 giai đoạn:
    1. Code completion/compilation
    2. Code execution

    Trong giai đoạn 1, tất cả các variables declared và function declared đều được
đưa lên đầu scope của nó. Điều này giúp tạo ra VARIABLE OBJECTS(cần tìm hiểu thêm) cho EXECUTION
CONTEXT(cần tìm hiểu thêm) của function trước khi được thực thi.
    Trong giai đoạn 2, các phép gán giá trị, code statement, function call được biên dịch theo
từng dòng.
```js
    year = 2021;
    console.log(year);
    var year;
//Trong đoạn code trên, phần khai báo biến year sẽ được chuyển lên trên đầu, cho nên output sẽ là 2021
```
    Để tránh gây ra lỗi, nên khai báo và gán giá trị cho biến cùng một lúc hoặc sử dụng strict mode.
    Khi khai báo các biến let hoặc const đều sẽ được đưa lên trên đầu nhưng nó sẽ không được phép dùng cho đến khi khai báo.
    Ngoài ra em có thắc mắc nếu Hoisting dễ gây ra lỗi và hạn chế dùng trong các dự án lớn, vậy tại
sao không loại bỏ nó ra khỏi JS. Thì tìm được lời giải thích, Hoisting không phải bug cũng như feature
mà là behavior của ngôn ngữ.

**Scope & Closure**
    Scope của JS có hai loại, đó là global và local. Tất cả các biến khi khai báo đề thuộc 1 trong 2
scope trên.
    Các function có thể truy cập các biến trong function(local) và ngoài function(global)

```js
    let a = 4;
    function sum(){
        let b = 2;
        return a +b;
    }
//Result: 6
```
