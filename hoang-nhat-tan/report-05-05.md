# Typescript

**Basic types**

- Trong TypeScript chia ra làm 7 loại cơ bản:
 + Boolean:

 ```js
 	var isTrue : boolean = true;
 ```
 + String:

  ```js
 	var aString : string = "Hello World";
 ```

 + Number:

  ```js
 	var x : number = 3333;
 ```

 + Array: có 2 cách khai báo array

  ```js
 	var list : boolean[] = [true, false];
 	var anotherList : Array<boolean> = [true, false]
 ```

 + Enum: khi khai báo enum cách phần tử sẽ được đánh số index từ 0 tăng dần

  ```js
 	enum Flowe{Whis, World, Wick};
 	var Flix = Flowe[2]; // Wick
 ```

 + Any: Any là một kiểu mà có thể gán bất kỳ kiểu nào cho nó

  ```js
 	var ex: any  = 4;
 	ex = "HHello Worldd";
 	ex = false;
 ```

 + Void: được sử dụng là đầu ra của hàm và giống với any

  ```js
 	function inforUser() : void {
 		alert("Hello User");
 	}
 ```

 **Function**

 - Giống với Js, TypeScript có 2 kiểu khai báo function là Named function và Anonymous function nhưng Ts hỗ trợ việc khai báo kiểu dữ liệu của input và output 

 ```js
 var add = function(x: number, y: number) : number{ return x + y; };
 ```
