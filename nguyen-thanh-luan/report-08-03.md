# NGUYỄN THÀNH LUÂN - Report 08/03:

# Day 2.
**Object, Prototype & Inheritance**
- Object: là tập hợp các thuộc tính được liên kết với nhau bằng tên và giá trị.
```js
    var myInfo = {
        name: 'Nguyen Thanh Luan',
        age: 28
    }
```
- Prototype: thuộc tính prototype cho phép thêm thuộc tính vào hàm tạo đối tượng.
```js
    function person(firstName, lastName)
    {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    person.Prototype.age = 28;
```
    Ngoài ra prototy cũng cho phép thêm phương thức vào đối tượng
```js
    function person(firstName, lastName)
    {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    person.prototye.name = function(){
        return this.firstName + " "+ this.lastName;
    }
```
- Inheritance: kế thừa trong javascript. Một đối tượng có thể kế thừa các thuộc tính của đối tượng khác thông qua từ khóa "extends".
         Trong class kế thừa cần gọi hàm "super()" để gọi ra constructor của class cha
```js
    class person
    {
        constructor(name)
        {
            this.name = name;
        }
    }
    class student extends person
    {
        super(name);
        constructor(univer)
        {
            this.univer = univer;
        }
    }
    let myInfo = student('Nguyen Thanh Luan', 'MTA');
```

**Condition statement (if...else, conditional (ternary) operator)**
    - Một số câu lệnh điều kiện: if...else, switch, while, do...while, for....
```js
    function myName(name) {
        if(condition) {
            statement1...
        } else {
            statement2....
        }
    }
```
    - Conditional (ternary) operator:
```js
    function myNum(num){
        return (num ? a : b)
    }

    // Hàm trên sẽ tương đương với
    if(a<b) {
        return a;
    } else {
        return b;
    }
```

**Data type: String, Number, Boolean, Null, Undefined, Symbol, Date, Object, Array**
    - Javascript có 2 nhóm dữ liệu: 
        + Primitives data: String, Number, Boolean, NUll, Undefined, Symbol, BigInt
        + Structurak data: Object ( Object and Array), Function.
    - Kiểm tra kiểu dữ liệu dùng "typeof"
```js
    var name = 'Nguyen Thanh Luan'; // String
    var num = 28; // Number
    var isTrue = true; // Boolean)
    var isNull = null;
    var name; // Undefined
    var id = Symbol('id'); // Symbol
    var newTime = new Date(); // Date
    var myInfo = { 
        name: 'Nguyen Thanh Luan',
        age: 28
    } // Object
    var myArr = [1,2,3]; // Array
```

**Immutable/Mutable, Pass by Value/Reference**
    - Immutable/Mutable
        + Object trong JavaScript là Mutable (trạng thái của object có thể thay đổi được)
        + Imutable: trường hợp muốn object không thay đổi được

        => Dùng: Object.defineProperty để gán giá trị mặc định
        Object.defineProperty(obj, prop, descriptor)
        + obj: đối tượng để xách định thuộc tính
        + prop: tên của thuộc tính xác định sửa, đổi
        + descriptor: Bộ mô tả cho thuộc tính đang được xác định hoặc sửa đổi.
```js
    const myInfo = {
        name: "Nguyen Thanh Luan",
        age: 28
    };
    Object.defineProperty(myInfo,"sex",{
        value: "Male",
        writable: false
    });
    myInfo.sex = "Female";
    console.log(myInfo); // Run => sex = Male
```
    - Pass by Value/Reference: khi 1 biến được khởi tạo, máy tính sẽ cung cấp 1 vùng trong bộ nhớ để lưu giá trị của biến
        + Pass by Value: đối với các loại dữ liệu nguyên thủy (Primitive Data Types): Value ở đây ám chỉ giá trị được lưu trong bộ nhớ
        + Pass by Reference: đối với loại dữ liệu đối tượng (Object Data Types): Reference ám chỉ tới vùng của bộ nhớ
    

