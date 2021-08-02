# NGUYỄN THÀNH LUÂN - Report 08/02:
# Day 1 + 2:
1. DỰ ĐịNH TÌM HIỂU.
* Hoisting
* Scope và Closure
* Object, Prototype & Inheritance
* Condition statement (if...else, conditional (ternary) operator)
* Data type: String, Number, Boolean, Null, Undefined, Symbol, Date, Object, Array
* Immutable/Mutable, Pass by Value/Reference

2. KẾT THÚC NGÀY.
**Hoisting**: hành vi mặc định của Javascript về việc di chuyển các khai báo lên đầu để compiled.
 ```js
        function hoisting()
        {
                console.log(fullName);
                var fullName = "Nguyen Thanh Luan";
        }
        // Hoisting ở đây là JavaScript sẽ đưa phần khai báo lên đầu là: "var = fullName"
        // Phần: = "Nguyen Thanh Luan" là gán giá trị
        // Run: Khai báo fullName mà không gán giá trị => undefined;

        function hoisting()
        {
                console.log(sum(1,2));
                function sum(a,b){
                        return a + b;
                }
        }
        // Declare function ở đây được coi như phần khai báo nên việc hoisting sẽ đưa cả hàm lên trên
        // Run => 3
        // let và const cũng được hoisting nhưng sẽ không được gán giá trị mặc định mà sẽ được đưa vào Temporal Dead Zone
```        

**Scope và Closure**:
        - Scope: phạm vi của biến:
                + Golobal: biến được khai báo toàn cục
                + Code block: biến được khai báo trong khối code
                + Local scope: được khai báo trong Hàm
        
```js
        var fullName = "Nguyen Thanh Luan";
        function scope()
        {
                console.log(fullName);
        }
        // Phạm vi biến khai toàn cục
        // Run => Nguyen Thanh Luan

        {
                let fullName = "Nguyen Thanh Luan";
                console.log(fullName); // Run => Nguyen Thanh Luan
        }
        consle.log(fullName) // Run => lỗi
        // Phạm vi biến trong code block áp dụng với let và const

        function scope()
        {
                var fullName = "Nguyen Thanh Luan";
                console.log(fullName); // Run => Nguyen Thanh Luan
        }
        // Phạm vi biến trong hàm
        // Nếu console.log(fullName) thực hiện bên ngoài hàm thì lỗi
```
        
        - Closure: làm tập hợp hàm và môi trường nơi hàm đó được khai báo và truy cập được biến ở bên ngoài phạm vi của nói

```js
        function counter()
        {
                let num = 0;
                function increCounter()
                {
                        return ++num;
                }
                return increCounter;
        }
        var result = counter();
        console.log(result()); // Run => 1
        console.log(result()); // Run => 2
```

**Object, Prototype & Inheritance**
        - Object: là tập hợp các thuộc tính được liên kết với nhau bằng tên và giá trị.
