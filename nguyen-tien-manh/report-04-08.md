# Nguyen Tien Manh - 04/08

## TOPIC: Các kiểu dữ liệu cơ bản trong Typescript

- Number: tất cả loại số (float, double, integer), ngoài hệ thập lục phân(hexadecimal) và thập phân(decimal literals), TypeScript còn hỗ trợ hệ nhị phân(binary) và bát phân)(octal literals)

```javascript
let decima: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

- String: "", '', `` (tất cả text)

```javascript
const fullName: string = "Manh";
let text: string = `Hello, my name is ${fullName}`;
// <=>
let text: string =
  "Hello, my name is " + fullName";
```

- Boolean: true, false (no truthy or falsy value)

```javascript
let isCompleted: boolean = false;
```

- Array: bất kì mảng javascript nào, type cũng có thể flexible

```javascript
const strArr: string[] = ["a", "b"];
strArr.map((item) => console.log(item));
let list: Array<number> = [1, 2, 3];
const strArr: any[] = ["a", 1, true];
```

- Tuple: tuple cho phép khai báo mảng với các giá trị có kiểu dữ liệu mà bạn đã biết, fixed-length.

```javascript
// Khai báo tuple
let x: [string, number];
// Khởi tạo đúng
x = ["hello", 10]; // OK
// Khởi tạo sai
x = [10, "hello"]; // Error
```

- Enums: kiểu dữ liệu đặc biệt cho phép một biến có thể là một tập hợp các hằng số định sẵn.

```javascript
enum Role {
  FRESHER = 'NEWBIE',
  JUNIOR = 100,
  SENIOR
};
```

- Any: bất kì loại giá trị nào, (khi data là một kiểu dữ liệu mà chúng ta không biết chắc chắn kiểu dữ liệu của nó) có thể dùng any.

```javascript
let notSureTypeValue: any = 10;
notSureTypeValue = "Là string"; // string
notSureTypeValue = false; // boolean
```

- Union

```javascript
function combine(input1: number | string, input2: number | string) {
  if (typeof input1 === "number" && typeof input2 === "number") {
    return input1 + input2;
  } else {
    return input1.toString() + input2.toString();
  }
}
```

- Void: hàm sẽ không trả về giá trị gì

```javascript
function displayInformation(): void {
  alert("Just only void function");
}
```

- Null và Undefined: có thể gán cho các kiểu dữ liệu khác

```javascript
let u: undefined = undefined;
let n: null = null;
```
