## TRAN DAI MINH 08-02

## TOPIC: Hoisting, Object, Prototype & Inheritance, Condition statement (if...else, conditional (ternary) operator), Data type: String, Number, Boolean, Null, Undefined, Symbol, Date, Object, Array.

- Hoisting: Nếu 1 biến được sử dụng sau đó mới khai báo và khởi tạo, giá trị khi nó được sử dụng sẽ là giá trị khởi tạo mặc định của nó ( undefined đối với một biến được khai báo bằng cách sử dụng var, nếu không thì chưa được khởi tạo).

```
console.log(name); // expected output: undefined
var name = 'Minh';
```

- Object là một thực thể độc lập, với thuộc tính và kiểu.

```
const name = {name: 'Minh'}
```

- Prototype & Inheritance

  - Prototype là cơ chế mà các object trong javascript kế thừa các tính năng từ một object khác.

  - Inheritance kế thừa trong OOP, bắt đầu có từ ES6

- Condition statement

  - If...else

```js
if (condition) {
  // statement true
} else {
  //statement false
}
```

- conditional (ternary) operator toán tử 3 ngôi.

```js
condition ? expression true : expression false
```

- Data type
  - String (chuỗi)
  - Number (số)
  - Boolean (true/false)
  - Null (giá trị Rỗng)
  - Undefined (khai báo nhưng chưa gán giá trị)
  - Symbol (kí tự)
  - Date (ngày tháng năm)
  - Array (Mảng)
