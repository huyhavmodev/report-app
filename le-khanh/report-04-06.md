# Destructuring Assignment

## **_Array_**:

- **_Array destructuring_**
  ```javascript
  let x = [1, 2, 3];
  let [a, b, c] = x;
  // a = 1
  // b = 2
  // c = 3
  ```
- **_Rest param in destructuring_**
  ```javascript
  let [a, ...b] = x; //
  // a = 1
  // b = [2,3]
  ```
- **_Default values_**
  ```javascript
  let [a = 10, b = 20, c = 21, d = 22];
  // a = 1
  // b = 2
  // c = 3
  // d = 22, x[3] = 22
  ```
- **_Nested array destructuring_**

  ```javascript
  let y = [1, 2, 3, [4, 5, 6]];
  let [a, b, c, [d, e, f]] = x;
  // a = 1
  // b = 2
  // c = 3
  // d = 4
  // e = 5
  // f = 6
  ```

- **_Ứng dụng_**:

  - _Swap variable_

  ```javascript
  let a = 10,
    b = 20;

  [a, b] = [b, a];

  // a = 20
  // b = 10
  ```

  - _Function return multi-value_

  ```javascript
  function stat(a, b) {
    return [a + b, (a + b) / 2, a - b];
  }
  let [sum, average, difference] = stat(20, 10);
  console.log(sum, average, difference); // 30, 15, 10
  ```

## **_Object_**:

- **_Object destructuring basic_**

  ```javascript
  let person = {
    firstName: "John",
    lastName: "Doe",
  };
  let { firstName: fname, lastName: lname } = person;
  // fname = "John"
  // lname = "Doe"

  let { firstName, lastName } = person; // rút gọn nếu variable name = property name
  ```

- **_Object destructuing seprate_**, khi tách lời khai báo và gán thì cần đặt trong ngoặc nếu không trình thông dịch sẽ trả về lỗi

  ```javascript
  let firstName, lastName;
  ({ firstName, lastName } = person);
  ```

- **_Object destructuring default value_**

  ```javascript
  let { firstName, lastName, middleName = "" } = person;
  ```

- **_Destructuring null object_**, gây lỗi ta cần dùng toán tử || để thay thế object null bằng object {}

  ```javascript
  let let {
  firstName,
  lastName
  } = null || {}
  ```

- **_Destructuring nested object_**

  ```javascript
  let employee = {
    id: 1001,
    name: {
      firstName: "John",
      lastName: "Doe",
    },
  };
  let {
    name: { firstName, lastName },
  } = employee;

  // get the name object
  let employee = {
    id: 1001,
    name: {
      firstName: "John",
      lastName: "Doe",
    },
  };

  let {
    name: { firstName, lastName },
    name,
  } = employee;

  console.log(firstName); // John
  console.log(lastName); // Doe
  console.log(name); // { firstName: 'John', lastName: 'Doe' }
  ```

- **_Object destructuring as function arguments_**

  ```javascript
  let display = ({ firstName, lastName }) =>
    console.log(`${firstName} ${lastName}`);

  let person = {
    firstName: "John",
    lastName: "Doe",
  };

  display(person);
  ```
