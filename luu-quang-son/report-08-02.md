# Day 1+2
**Hoisting**
    Hoisting là cơ chế của JavaScript cho phép các khai báo biến hoặc hàm được dời lên trên đầu phạm vi của chúng trước khi thực thi đoạn code.(chỉ di chuyển phần khai báo)
    -- Hoisting đối với biến hoặc hàm:
```js  
        function hoisting(){
            var name = "this is hoisting";
            console.log(name);
        }
            hoisting(); /// hoisting
``` 
    --  Hoisting còn có thứ tự ưu tiên như :
     1.Gán biến ưu tiên hơn khai báo hàm.  
     2.Biểu thức hàm ưu tiên hơn khai báo biến.
     3.Khai báo hàm ưu tiên hơn khai báo biến.



**Scope và Closure**
        **Scope** là các loại phạm vi mà bạn có quyền truy cập và khi gọi mỗi hàm thì luôn có phạm vi mới được tạo ra . Các loại phạm vi:
         1.Global Scope : có thể truy cập được ở bất cứ đâu.
```js   
        var message = "Scope";
        function logger(){
            console.log(message);
        }
        logger(); ///Scope
```

        2.Code block : chỉ cho phép truy cập trong 1 khối ({}).
```js   {
            let age = 30;
        }
        console.log(age); ///30
```

        3.Local Scope : phạm vi được tạo ra khi hàm đó được gọi. 
```js  
        function logger(){
            var name = "Quang Son";
         console.log(name);
}
        logger();   /// Quang Son.
    ///  console.log(name); ngoài Logger =>> error.
```


        **Closue** là 1 hàm có thể ghi nhớ nơi nó được tạo và truy cập  được biến ở ngoài phạm vi của nó.
```js   
         function secret(secretCode) {
            return {
          saySecretCode () {
             console.log(secretCode);
            }
          }
        }
        const theSecret = secret("CSS Tricks is amazing");
        theSecret.saySecretCode();
// "CSS Tricks is amazing"
```

**Object, Prototype & Inheritance**

    Object là một danh sách các item, mỗi item là một cặp name-value, trong đó value có thể là: các kiểu dữ liệu cơ bản, function, hay cũng có thể là một object khác (kiểu dữ liệu phức hợp).
```js  var Object = {
    id : 1;
    name = "car";
};
```

    Prototype là cơ chế mà các object trong javascript kế thừa các tính năng từ một object khác.
```js
        function Person(age,name){
            this.age = age;
            this.name = name;
}
    newPerson = new Person(18,'Son');
    console.log(newPerson);
        ///Person {age: 18, name: "Son"}
```

    Inheritance là kế thừa. Có 3 cách kế thừa cơ bản: 
    - Kế thừa cơ bản: kế thừa các phương thức và thuộc tính của lớp cha nhưng không kế thừa prototype
    - Kế thừa prototype: kế thừa các phương thức và thuộc tính của lớp cha cùng với prototype
    - Kế thừa với từ khóa class, extends trong ES6: tương tự như kế thừa prototype nhưng cách viết ngắn gọn, trực quan hơn.
```js
		class Game{
			constructor(name){
				this.gameName = name;
			}
			get gname(){
				return this.gameName;
			}
			set gname(x){
				this.gameName = x;
			}
		}
		let newGame = new game("LOL");
```
    
    
