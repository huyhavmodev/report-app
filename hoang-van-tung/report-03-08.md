# REPORT DAY - 08/03

## Hoàng Văn Tùng - 08/03

### Day 1 + 2

**Hosting**

Trong giai đoạn tạo thì javascript sẽ di chuyển các khai báo biến lên đầu của đoạn mã, giúp cho chương trình không bị lỗi khi sử dụng biến trước khi khai báo.

```js
function hoist() {
    var message='Hoisting!'
    return (message);
}

hoist(); // Ouput: Hoisting!
```

**Scope and Closure**

*Trong JS, scope đề cập đến ngữ cảnh hiện tại trong code của bạn. Scope có thể được xác định trên globally hoặc locally* 

- Golbal Scope

```js
    // global scope
    var name = 'Tung';
```
- Local Scope

```js
        // Scope A: đây là global scope 
    var myFunction = function () {
        // Scope B: đây là Local scope
    };
```

*Closure là một hàm được tạo ra từ bên trong một hàm khác, nó có thể sử dụng các biến toàn cục, biến cục bộ của hàm cha và biến cục bộ của chính nó.*

```js
function sayHi(name){
    let say = function(){
        alert("Xin chào, tôi là " + name);
    };
    return say;
}
```
*Trong ví dụ này thì hàm say() chính là một closure function. Bên trong nó có thể sử dụng được biến của hàm cha name.*

**Object, Prototype & Inheritance**

*Object*
- Object: Object as literal: Sử dụng cặp dấu ngoặc {} và bên trong đó là danh sách các property, method của object.
- Object.create: Sử dụng Object.create để tạo một object mới với proto trỏ tới object ban đầu.
- Function constructor: Tạo object bằng việc sử dụng từ khóa new. Object mới sẽ có proto trỏ tới prototype của function tạo ra nó.

*Prototype*

Prototype là cơ chế mà các object trong javascript kế thừa các tính năng từ một object khác. Tất cả các object trong javascript đều có một prototype, và các object này kế thừa các thuộc tính (properties) cũng như phương thức (methods) từ prototype của mình.

```js
//Tạo ra 1 mẫu khởi tạo, cũng là tạo ra 1 prototype object
function Person(_age, _name){
   this.age = _age;
   this.name = _name;
}
 
//Có thể thêm thuộc tính vào thuộc tính prototype của hàm khởi tạo
Person.prototype.height = 0;
 
//Tạo ra 1 instance của Person
//Có cả 3 thuộc tính của mẫu khởi tạo Person
var jack_person = new Person(10, "Jack");
for (var att in jack_person){
   console.log(att);
}
 
//Xem đối tượng prototype của instance vừa tạo
jack_person.__proto__;
```
*Inheritance*

**Condition statement (if...else, conditional (ternary) operator)**
	- Use if to specify a block of code to be executed, if a specified condition is true.
```js
	if(condition){
		...
	}
	else if{
		...
	}
	else{
		...
	}
```
- Else to specify a block of code to be executed, if the same condition is false.
- Else if to specify a new condition to test, if the first condition is false
- Switch to specify manny alternative blocks of code to be executed

**Data type: String, Number, Boolean, Null, Undefined, Symbol, Date, Object, Array**


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