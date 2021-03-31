# JS Summary

## 1.Hoisting

### là hành vi mặc định của js tách riêng việc tạo ra hàm và biến thành 2 phần: phần khai báo với phần gán giá trị, sau đó phần khai báo luôn được đẩy lên đầu của scope và khởi tạo. Vì js hoạt động đơn luồng nên mọi lời khai báo khi complie nó phải đưa lên đầu để tránh việc khi complie bị lỗi

- Vì vậy biến có thể khai báo sau dùng trước;
- Riêng với let và const khai báo sau dùng trước có thể gây ra lỗi.
  - Với let và const phần khai báo cũng được đẩy lên đầu nhưng chưa khởi tạo, cho tới khi trình biên dịch chạy tới dòng mà let và const được khai báo nó mới có thể được sử dụng
- Chỉ có phần khai báo được đưa lên trước, phần gán giá trị được đưa lên sau
- Phần khai báo hàm được đưa lên trước phần khai báo biến

## 2.Scope và Closure

### Scope: là phạm vi mà tại đó một hàm hoặc một biến có thể truy cập hoặc sử dụng được.

- Khi khai báo biến cùng scope trùng tên thì sẽ gây lỗi với let và const nhưng với var thì nó sẽ ghi đè
- Global Scope: một hàm hoặc một biến được khai báo toàn cục thì nó có thể được dùng trong tất cả các
- Local Scope: Có 2 loại là function scope và block scope
  - Function Scope: một biến được khai báo cục bộ thì nó chỉ có thể được dùng trong nội bộ của hàm chứa nó.
  - Block Scope: dùng cho let và const biến khi khai báo trong dấu ngoặc nhọn {} sẽ chỉ có thể sử dụng trong ngoặc đó

### Closure

- Khi tạo một function trong một function khác thì được gọi là closure.
- Các biến trong outer function có thể được dùng trong closure nhưng ngược lại thì không.

## 3.Object, Prototype, inheritance

### Object: trong js hầu hết mọi thứ đều là object, ngoại trừ các giá trị nguyên thủy

- Với biến ta có thể lưu trữ một giá trị, nhưng với object ta có thể lưu trữ rất nhiều giá trị, mỗi giá trị được viết theo cặp thuộc tính và giá trị, cách biệt nhau với dấu “ : ” và mỗi cặp tách biệt nhau bởi dấu “ , ”
- Giá trị ở đây ngoài những kiểu cơ bản ra cũng có thể là function
- Khởi tạo Object:
  - Bằng diễn giải, là viết list các cặp giá trị của Object trong dấu “ { } ”
  - Bằng từ khóa new Object()
  - Bằng hàm khởi tạo constructor
- Js Object có thể tùy biến, chúng được dùng theo tham chiếu, không phải gán giá trị, ta không thể gán 1 object cho một object khác, đó chỉ tạo tham chiếu tới object mà nó trỏ tới
- Truy cập các property của Object theo cú pháp:
  - objectName.property
  - objectName[“property”]
  - objectName[expression]
- Thêm một property mới:
  - objectName.newProp = value
- Xóa một property:
  - delete objectName.property
  - delete objectName[property]
- Các thuộc tính của property:
  - Value, enumerable, configurable, writable
- Object method: phương thức của object trong js là một function được lưu trong một thuộc tính của Object
  - Để chạy hàm ta dùng syntax: objectName.methodName( ), nếu không dùng dấu “ ( ) ” js sẽ hiểu là ta đang lấy định nghĩa của function đó chứ không thực thi
  - Các thêm method vào Object tương tự như các thêm giá trị cho property
- get/set với các ngôn ngữ lập trình bậc cao khác luôn có các hàm get set để truy cập dữ liệu của các Object để đảm bảo tính đóng gói dữ liệu, js cũng có tính năng vậy.

  - Ngoài dùng một thuộc tính và truyền cho nó định nghĩa một function thì ta có thể dùng từ khóa set và get
  - Syntax:

    ```javascript
        objectName = {
            propertyName =  value,
            get funcGetName (){
                return this.propertyName;
            },
            set funcSetName ( value ){
                this.propertyName = value;
            }
        }
    ```

  - Sử dụng:
    ```javascript
    objectName.funcGetName;
    objectName.funcSetName(value);
    ```
  - Có thể dùng _Object.defineProperties_, _Object.defineProperty_, _Reflect.defineProperty_ để thêm get set cho object, các property được thêm theo các này tự động được định nghĩa **_writable : false_**.

- Object contructor: là một hàm dùng để khởi tạo một hoặc nhiều object với cùng một kiểu
  - Dùng từ khóa new để tạo một object mới với contructor function. Syntax:
  ```javascript
      function Contructor ( value1, value2, … ){
          this.propertyName1 =  value 1;
          this.propertyName2 = value 2;
          // ...
      }
      objectName = new Contructor( value1 , value2, … )
  ```
- `Prototype` là một property mà mọi Object trong js được kế thừa, nó bao gồm các thuộc tính cũng như các function được js định nghĩa trước (build-in function) như touppercase,…
- Với mọi object trong js đều kế thừa property và method từ một `**prototype` nào đó như Date object từ `Date.prototype`, Array object từ `Array.prototype`,… và tất cả đều kế thừa prototype từ `Object.prototype`.
- Ta có thể thêm cũng như chỉnh sửa các `property` và `method` cho constructor qua `prototype`, syntax:
  ```javascript
      Constructor.prototype.property = value.
      //property có thể là property đã tồn tại hoặc chưa
      //value có thể là giá trị hoặc function
  ```
- Với các object ta cũng có thể chỉnh sửa cũng như thêm property cho prototype qua `__proto__`, syntax:
  ```javascript
  objectName.__proto__.property = value;
  //property có thể là property đã tồn tại hoặc chưa
  //value có thể là giá trị hoặc function
  ```
- Khi một object truy cập tới một property hoặc method có trong prototype thì không cần phải dùng từ khóa prototype hay `__proto__` ta có thể truy cập thẳng tới method hoặc property đó.
- Và tránh việc chỉnh sửa các prototype của `Object.prototype` vì làm vậy sẽ khiến tất cả các object có thể sẽ không nhận property hoặc method mặc định của js, điều này có thể gây ra lỗi hoặc chương trình cho ra kết quả không như mong muốn.
