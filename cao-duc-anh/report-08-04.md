**Object, Prototype & Inheritance**
- Trong JS, gần như mọi thứ đều là Object.
    + Booleans, Numbers, Strings đều có thể là Object nếu đựợc khai báo với keyword NEW.
        Emxample:
        ```js
        var booleans = new Boolean;
        var numbers = new Number;
        var strings = new String;
        ```
    + Dates, Maths, Regular expressions, Array, Functions và Objects luôn là object.
    Vậy Object là một tập hợp bất kỳ các tính chất, đặc tính. 

- Prototype là một Object khác được sử dụng như các tính chất(properties) dự phòng.
Khi một object nhận yêu cầu gọi một property mà nó không có, nguyên mẫu(prototype) của object
sẽ tìm kiếm property đó trong prototype của nó rồi nếu không có, nó sẽ tiếp tục tìm. Điều này liên quan đến Prototype Chain.


    ```js
    let emptyObj = {};
    console.log(emptyObj.toString);
    /*Sẽ đưa ra kết quả là ƒ toString() { [native code] }, 
    em để câu vừa rồi tìm hiểu saudo không muốn bị chậm tiến độ */
    console.log(emptyObj.toString());
    // Kết quả trả về lúc này sẽ là [object Object]
    ```
    Ở đây, kết quả trả về là [object Object] do prototype đầu tiên của tất cả các Object chính là Object.prototype.
    Như đã nói ở trên, quá trình tìm properties sẽ liên tục tìm cho đến khi tìm thấy hoặc sẽ dẫn đến Object và nếu Object không có, thì tức là properties đó không có.
    Khi em thử console.log(object Object) ra thì nhận được một kết quả khá là khó hiểu, em sẽ tìm hiểu dần sau.

- Inheritance là việc Object có thể truy cập vào các phương thức(method) và thuộc tính(properties) của các Object khác.
Object có thể kế thừa nhiều thứ từ các object khác.

**Codition statement**
- If sẽ thực thi block code khi điều kiện thoả mãn(true) và else sẽ thực thi một đoạn code khi điều kiện kia không thoả mãn(false)
Ngoài ra còn có switch là các đoạn code luân phiên nhau được thực thi.
- Conditional (ternary) operator là một câu điều kiện với dấu hỏi(?), expression thực thi nếu điều kiện là true, sau đó là dấu hai chấm(:)
Nếu điều kiện là false. Đây thường được dùng như câu lệnh rút ngọn của IF

    ```js
    function checkAge(age) {
        return (age >= 18 ? "Du tuoi xem" : "Chua du tuoi");
    }
    var userAge = 17;
    console.log(checkAge(userAge));
    // => Chua du tuoi
    ```

**Data type**

|   Data Types   |   Description                          		|   Example    |
|----------------|----------------------------------------		|--------------|
|String	         |Textual data                            		|'Hello world!'|
|Number          |An interger or a floating-point number  		|3; 3.14;...   |
|BigInt          |An interger with arbitrary precision    		|1n,...        |
|Boolean         |Any of two values: true or false        		| true & false |
|undefined       |A data type whose variable is not initialized | var x        |
|null 			 |Denotes a null value 							| let x = null;|
|symbol			 |Data type whose instance are unique are unique and immutable|
|object 		 | key-value pair of collection of data         |let game = {};|

**Immutable/Mutable, Pass by Value/Reference**
- Trong JS, các primitive type đều là không thể thay đổi. Ví dụ như kiểu String và Number,
vì các kiểu này được PASS BY VALUE. Nghĩa là mỗi khi có một giá trị được gán, thì sẽ có một
bản sao chép của giá trị đó được tạo ra.
    
```js
let a = 1;
let b = a;
```
    Khi gán giá trị của biến a cho b, 1 đã được sao chép, và gán cho b. Nên nếu thay đổi biến a sẽ không ảnh hưởng đến biến b.
- Ngược lại, Array và Object có thể thay đổi vì chúng được PASS BY REFERENCE. Tức là chúng cùng được
gán vào một ô nhớ có cùng giá trị. Cho nên khi thay đổi giá trị của ô nhớ đó, thì các Array và Object cũng thay đổi theo.
```js
var x = {
    name: "Duc Anh"
}
var y = x;
x.name = "Cao Duc Anh";
//lúc này y.name cũng sẽ được thay đổi thành Cao Duc Anh
```
**This, apply, call, bind**
    - This là keyword đại diện cho Object mà nó thuộc về. Trong một METHOD, this là đại diện cho Object sở hữu method đó.
Khi đứng một mình, this đại diện cho Global Object. Trong function, this đại diện cho Global Object nhưng khi ở strict mode, this trong function là undefined.
Trong một EVENT, this đại diện cho ELEMENT ảnh hưởng bởi EVENT đó.
    - Những method như call(), apply() có thể khiến this đại diện cho bất kỳ Object nào.
```js
    const person = {
        firstName: "Duc Anh",
        lastName: "Cao",
        age: 24,
        fullName : function() {
            return this.firstName + " " + this.lastName;
        }
    }
```
    -Trong trường hợp trên, this là đại diện cho chủ sở hữu của method fullName và đó là person.

```js
    <button onclick="this.display='none'">
        Click to hide button!
    </button>
```
    - Trong trường hợp trên, this đại diện cho element ảnh hưởng bởi event onclick.

    - Call(), Apply() có thể viết method mà dùng được cho các Object khác nhau.
    - Hàm Call() có thể gọi một method và dùng nó cho một Oject khác, có thể truyền vào đó arguments.
```js
    const person = {
        fullName : function() {
            return this.firstName + " " + this.lastName;
        }
    }

    const person1 = {
        firstName : "Duc Anh",
        lastName : "Cao"
    }
    //Object 1 không hề có method fullName nhưng ta có thể sử dụng nó với hàm Call()
    person.fullName.call(person1,24,"tuoi");
    // => Cao Duc Anh, 24, tuoi
```
    - Hàm Apply() cũng tương tự như hàm Call().
```js
    person.fullName.apply(person1);
    // => Cao Duc Anh
```
    - Hàm Apply() khác hàm Call() ở chỗ, hàm Call() nhận arguments riêng biệt còn hàm Apply() nhận arguments là một array.
```js
    person.fullName.call(person1,24,"tuoi");
    person.fullname.apply(person1, [24, "tuoi"]);
    // => Cao Duc Anh, 24, tuoi
```

    - Bind() là hàm dùng để gán dữ liệu vào đối tượng this của hàm đang sử dụng và cũng giúp dùng được các method, function từ một Object khác.
```js
    const user = {
        person : {  fullName : "Cao Duc Anh",
                    age : 24,
        },
        showInfo: function(event) {
            console.log(this.person.fullName + " " + this.person.age);
        }
    }

    $ ("button").click (user.showInfo);
    // Đoạn code trên khi chạy sẽ báo lỗi vì this đã đại diện cho element button chứ không phải là user nữa.
    $ ("button").click (user.showInfo.bind(user));
    //Đoạn code trên bind() sẽ gán giá trị this cho User.
```
