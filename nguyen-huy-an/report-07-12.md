# Nguyen Huy An - 07/12

## AJAX and JSON


### AJAX
- AJAX allows web pages to be updated asynchronously by exchanging data with a web server behind the scenes. This means that it is possible to update parts of a web page, without reloading the whole page.
- Điều này giúp tăng trải nghiệm người dùng và tránh được những render dư thừa trong quá trình làm việc với server


#### Ưu điểm:
- Cải thiện trải nghiệm người dùng
- Tăng khả năng tương thích
- Hỗ trợ xử lý bất đồng bộ
- Giảm mức xử dụng băng thông và tăng tốc độ
- Năng suất người dùng được nâng cao

### Nhược điểm:
- Tính không tương thích cho trình duyệt: Các trình duyệt không hỗ trợ JavaScript hoặc tắt tùy chọn JavaScript sẽ không thể sử dụng chức năng của nó.
- Không an toàn: Trang web có thể khó gỡ lỗi, tăng kích thước mã của trang web và khiến trang web dễ bị đe dọa bảo mật nghiêm trọng.
- Bookmark: Khi sử dụng ajax sẽ ảnh hưởng đến người dùng vì không thể bookmark lại trang có ajax được.


### JSON
- JSON is a text format for storing and transporting data. JSON is "self-describing" and easy to understand
- Mỗi info sẽ có 2 phần là key và value, trong đó có 1 số quy tắc nhất định.
- khi làm Ajax thì ở phía API sẽ trả về nguyên đoạn mã HTML luôn, điều này sẽ tốn tài nguyên hệ thống vì nó sẽ phải gửi luôn những đoạn mã HTML không cần thiết. Vậy giải pháp là các API sẽ gửi về một danh sách dữ liệu ở định dạng JSON, sau đó ở phía client sẽ sử dụng Javascript để tạo nên các thẻ HTML cần thiết theo yêu cầu của chức năng đó.


## Promise and Async await


### Promise:
- A Promise is a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.

- A Promise is in one of these states:

+ pending: initial state, neither fulfilled nor rejected.
+ fulfilled: meaning that the operation was completed successfully.
+ rejected: meaning that the operation failed

- We can use chain promises. There are some methods used to associate further action with a promise that becomes settled: promise.then(), promise.catch(), and promise.finally().. In here I just focus on .catch() and .then()

+ The .then() method takes up to two arguments; the first argument is a callback function for the resolved case of the promise, and the second argument is a callback function for the rejected case. Each .then() returns a newly generated promise object, which can optionally be used for chaining.
+ On the other hand, in the absence of an immediate need, it is simpler to leave out error handling until a final .catch() statement. A .catch() is really just a .then() without a slot for a callback function for the case when the promise is resolved.


### Async await:
- Async: makes a function return a Promise
- Await: makes a function wait for a Promise

Ex:
```javascript
    async function myDisplay() {
  let myPromise = new Promise(function(myResolve, myReject) {
    setTimeout(function() { myResolve("Hello !!"); }, 3000);
  });
  document.getElementById("demo").innerHTML = await myPromise;
}

myDisplay();
```

## ES6
- 1 số tính năng mới được thay đổi trong ES6:

### Scope
- Block Scope Variables:
 + let: có phạm vi hoạt động trong block scope mà nó được khai báo hoặc các block-scope được nó block-scope khai báo nó bên ngoài, còn các block scope bao ngoài scope chứa nó sẽ không sử dụng được. không có hoisting

- Block Scope Functions: tương tự như block scope variable

### Arrow function:
- 1 số lưu ý: 
+ không dùng như constructor
+ không dùng yield mà không có body của nó
+ không phù hợp với bind, call, apply

- cấu trúc:
+ param => expression
+ (param1, paramN) => expression

### Template Literals
- Giúp tạo chuỗi nhiều dòng và nội suy chuỗi
- Sử dụng kí tự `` thay vì '' và ""
- Các biến, biểu thức có thể được đặt trong cú pháp ${...} => giúp biểu thức gọn nhẹ, dễ đọc hơn

Ex: `Tổng của ${a} và ${b} là ${a+b}` thay vì "Tổng của" + a + "và" + b + "là" + sum

### Default Parameter Value
- Gán giá trị mặc định cho biến

```javascript
function myFunc (x,y=10){
    return x+y;
}
myFunc(5) //15
```

### Destructuring
- Destructuring là một cú pháp cho phép gán các thuộc tính của một Object hoặc một Array. Điều này có thể làm giảm đáng kể các dòng mã cần thiết để thao tác dữ liệu trong các cấu trúc này. 
- Có hai loại Destructuring: Destructuring Objects và Destructuring Arrays.

- 1 số ví dụ về kĩ thuật destructuring

+ Variable assignment   
```javascript
const res = [1, 2, 3, 4,] 
const [a, b, c] = res
console.log(a, b, c);//1 2 3
```
+ Swapping
```javascript
var a = 1;
var b = 2;
[a, b] = [b, a]
console.log(a, b) ;//2, 1
```

+ Ignoring values 
```javascript
const res = () => [1, 2, 3]
const [a, ,b] = res()
console.log(a, b) ;//1,3
```

+ Assignment to new variables: Gán giá trị cho một biến mới
```javascript
const res = {blog: 'anonystick.com', type: 'javascript'}
const {blog: nameBlog, type: newType} = res;
console.log(nameBlog, newType);//anonystick.com, javascript
```
### Spread operator

- Cho phép duyệt qua phần tử và truyền vào phương thức như đối số
- Là một cách rất hữu dụng và ngắn gọn để dùng trong các thao tác với mảng như thêm phần tử vào mảng, kết hợp mảng (hoặc object), truyền tham số mảng vào function

+ Tìm số lớn nhất trong mảng
```javascript
Math.max(...[1,3,5]) // output: 5
```

+ Sao chép mảng (có thể dùng khi truyền tham chiếu)
```javascript
const arr1 = [1,2,3,4]
const arr2 = [...arr1] // [1,2,3,4]
```

+ Thêm phần từ vào mảng 
```javascript
const arr1 = [1,2,3,4]
const arr2 = [9,10,...arr1]
```

Ngoài ra còn có khá nhiều ứng dụng nhưng cơ bản đều dựa theo cách làm trên

### Rest parameter
Tương tự như spread nhưng ngược lại. Định nghĩa 1 hàm với số lượng tham số có thể thay đổi tùy ý

```javascript
function sum(...theArgs) {
  return theArgs.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(1, 2, 3));
// expected output: 6

console.log(sum(1, 2, 3, 4)); // truyền vào tùy ý số lượng biến
// expected output: 10
```