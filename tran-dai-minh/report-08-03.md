## TRAN DAI MINH 08-03

## TOPIC: Scope và Closure, Immutable/Mutable, Pass by Value/Reference, this, apply, call, bind, setTimeout/clearTimeout, setInterval/clearInterval.

- Scope: có 2 loại scope là: global scope và local scope.

  - **Global Scope** nếu 1 biến được khai báo ở ngoài tất cả các hàm thì được coi là **global scope** (phạm vi toàn cục).

```
var name = 'Minh'
```

- **Local scope** là những biến chỉ sử dụng được trong 1 phần củ thể thì được coi là **local scope**.

```
var name = 'hoang';
function run(){
  var name = 'Minh';
  console.log(name);
}
run(); // expected output: Minh.
console.log(name); // expected output: hoang.
```

- Closure: khi nào tạo một **function** trong một **function** khác, bạn đã tạo một **Closure**.

```
function outerFunction () {
  const outer = "I see the outer variable!";

  return function innerFunction() {
    console.log(outer);
  }
}

outerFunction()(); // expected output: I see the outer variable!
```

- Immutable/Mutable:

  - **Immutable** là các đối tượng có trạng thái không thể thay đổi sau khi đối tượng được tạo (các giá trị nguyên thuỷ: string, number, boolean).

```
var a = 10;
```

  - **Mutable** là một loại biến có thể thay đổi được.

```
let b = {name: 'Minh', age: 20};
b.name = 'hoa'; // thay doi doi tương object b.
```

- Pass by Value/Reference:

  - Khi bạn truyền một biến trỏ đến một biến nguyên thủy chẳng hạn như 'hi', giá trị sẽ được sao chép vào một biến cục bộ mới bên trong hàm.

```
let name = 'Minh';
function changeName(name) {
  name = 'Minh dep trai';
}
console.log(name); // expected output: 'Minh'
```

- Khi bạn truyền một biến trỏ đến một đối tượng, tham chiếu đến đối tượng sẽ được chuyển vào hàm để một biến cục bộ mới trỏ đến cùng một đối tượng.

```
let actress = {
  name: 'Minh'
};
function changeActress(act) {
  act.city = 'Arizona';
}
changeActress(actress);
console.log(actress); // expected output: { name: 'Minh', city: 'Arizona' }
```

- This: từ khoá **this** trong Javascript đề cập đến đối tượng mà ó thuộc về.

```
const test = {
  prop: 42,
  func: function() {
    return this.prop;
  },
};

console.log(test.func());
// expected output: 42
```

- Apply: là phương pháp gọi một hàm với một định **this** giá trị, và **arguments** được cung cấp như là một mảng.

```
const numbers = [5, 6, 2, 3, 7];

const max = Math.max.apply(null, numbers);

console.log(max);
// expected output: 7
```

- Call: gọi một hàm với giá trị của **this** và các đối số riêng lẻ.

  - Syntax: **function.call(thisArg, arg1, arg2, ...)**

```
function Product(name, price) {
    this.name = name;
    this.price = price;
}

function Food(name, price) {
    Product.call(this, name, price);
    this.category = 'food';
}

console.log(new Food('cheese', 5).name);
// expected output: "cheese"
```

- Bind: được dùng để xác định tham số **this** cho một **function**.

  - Syntax: **bind(thisArg, arg1, ... , argN)**

```
const module = {
  x: 42,
  getX: function() {
    return this.x;
  }
};

const unboundGetX = module.getX;
console.log(unboundGetX()); // The function gets invoked at the global scope
// expected output: undefined

const boundGetX = unboundGetX.bind(module);
console.log(boundGetX());
// expected output: 42
```

- SetTimeout/clearTimeout

  - **SetTimeout** được sử dụng nếu bạn muốn hàm của mình thực thi bao nhiêu mili giây kể từ khi gọi method **setTimeout()**.

  - Syntax: **setTimeout ( expression, timeout )**.

```
var timeoutId = setTimeout(function(){ alert("Hello"); }, 1000);
// expected output: Display an alert box after 1s (1000 milliseconds):
```

- **clearTimeout** sẽ xoá đi nhiệm vụ mà ta đã thiết lập trong hàm **setTimeout()**

- Syntax: **clearTimeout(myTimeOut)**.

```
  clearTimeout(timeoutId);
```

- SetInterval/ClearInterval:

  - **SetInterval** hàm này sẽ thường được sử dụng để thiết lập độ trễ cho các hàm sẽ được thực hiện lặp lại như là hiệu ứng.

  - Syntax: **setInterval(function, milliseconds, param1, param2, ...)**

```
var intervalId = setInterval(function(){ alert("Hello"); }, 3000);
// expected output: alert("Hello");
```

- **ClearInterval** sẽ xóa đi nhiệm vụ mà ta đã thiết lập trong hàm **setInterval()**.

- Syntax: clearInterval(mySetInterval);

```
  clearInterval(intervalId);
```
