## TRAN DAI MINH 08-04

## TOPIC: Array, Linked list, Queue, Stack, Hash table, Set, Tree, Graph, AJAX and JSON, promise, async await syntax, ajax request (Fetch API, Axios), scope, arrow function, template string, destructuring, default parameter, rest, spread.

- AJAX Là viết tắt của cụm từ Asynchronous Javascript and XML. Là phương thức trao đổi dữ liệu với máy chủ và cập nhật một hay nhiều phần của trang web giúp chúng ta tạo ra sự sinh động cho Website của mình mà không reload lại trang.

- JSON là chữ viết tắt của Javascript Object Notation, là một dạng dữ liệu tuân theo một quy luật nhất định mà hầu hết các ngôn ngữ lập trình hiện nay đều có thể đọc được, bạn có thể sử dụng lưu nó vào một file, một record trong CSDL rất dễ dàng.

- **promise** là cơ chế giúp thực thi các thao tác bất đồng bộ mà không vị rơi vào callback hell.

```js
function getData() {
  return new Promise(function (resolve) {
    axios.get('http://json').then(function (result) {
      return result;
    });
  });
}
```

- **async** được dùng để khai báo một **function** bất đồng bộ, khi gọi tới hàm async nó xử lý mọi thứ và trả về kết quả trong function của nó.

- **await** tạm dừng thực hiện các function async.

```js
async function getData(){
  let data = await.axios.get('http://json');
  return data;
}
```

- ajax request (Fetch API, Axios)

- **arrow function** là cú pháp ngắn ngọn hơn để dùng **function**, sử dụng **=>**.

```js
const person = (name,age) => {
    console.log('Name:'+ name + age +years old);
}
person('Minh',18);
//expected output: Name: Minh 18 years old;
```

- **template string** là cách mà chúng ta tạo ra một string dễ dàng hơn với các biến, biểu thức bên trong string.

```js
const name = 'Minh';
var person = `My name is ${name} `;
```

- **destructuring** là một cú pháp cho phép tách dữ liệu được lưu trữ bên trong Objects hoặc Arrays và gán chúng cho các biến riêng biệt.

```js
//destructuring object
const person = { name: 'Minh', age: 20 };
const { name, age } = person;
console.log(name); // expected output: Minh
console.log(age); // expected output: 20

//destructuring array
const animals = ['dog', 'cat'];
const [one, two] = animals;
console.log(one); // expected output: dog
console.log(two); // expected output: cat
```

- **default parameter** là các tham số của function được khởi tạo với giá trị mặc định hoặc undefined.

```js
function main(a, b = 1) {
  return a + b;
}
main(3); // expected output: 4
```

- **rest** là cú pháp cho phép nhận các đối số của function dưới dạng mảng.

```js
function main(...rest) {
  console.log(rest);
}
main(1, 2, 3, 4, 5); // expected output: [1,2,3,4,5]
```

- **spread** là cú pháp cho phép sao chép array, tách or kết hợp một hay nhiều array, thêm một item vào 1 list, kết hợp các object.

```js
const animals = ['dog', 'cat', 'mouse'];
const moreAnimals = [...animals];
console.log(moreAnimals); // expected output: 'dog', 'cat', 'mouse'

//add item to array
const animals = ['dog', 'cat', 'mouse'];
const moreAnimals = ['bird', ...animals];
console.log(moreAnimals); // expected output: 'bird','dog', 'cat', 'mouse'
```
