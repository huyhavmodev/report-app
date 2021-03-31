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
- Với mọi object trong js đều kế thừa property và method từ một `prototype` nào đó như Date object từ `Date.prototype`, Array object từ `Array.prototype`,… và tất cả đều kế thừa prototype từ `Object.prototype`.
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

## 4.Condition Statements

### Là những câu lệnh điều hướng xử lý theo các lựa chọn hay điều kiện khác nhau

- `If-else`
  - Chỉ ra đoạn code nào sẽ được thực hiện nếu thỏa mãn một điều kiện cụ thể nào đó.
  - Với if đoạn code sẽ chạy nếu điều kiện đặt ra thỏa mãn.
  - Với else đoạn code sẽ chạy nếu thỏa mãn điều kiện đối nghịch với điều kiện của if.
  - Với else if đoạn code sẽ chạy nếu thỏa mãn điều kiện đối nghịch với if và thêm một điều kiện nữa mà else if đặt ra
- `Switch`
  - Chỉ ra một chuỗi các đoạn code nào sẽ được thực hiện nếu giá trị kiểm tra bằng đúng với giá trị mà ta chỉ định.
  - Với case là các giá trị mà nếu bằng đúng với nó thì tất cả các đoạn code kể từ case đó trở đi sẽ được thực hiện.
  - Nếu có break trong case switch sẽ tự thoát khi mà case đúng nếu không tất cả các case xếp dưới kể từ case đó sẽ được thực hiện.
  - Với default là đoạn code mà sẽ được thực thi nếu không có case nào đúng
  - Nếu có nhiều case đúng thì case đầu tiên sẽ được lựa chọn.
  - Và so sánh trong switch là so sánh đúng kiểu đúng giá trị.
- Ternary operator
  - Là toán tử điều kiện syntax:
    ```javascript
    condition ? exIfTrue : exIfFalse;
    ```
    - Nếu điều kiện đúng sẽ thực hiện exIfTrue.
    - Nếu điều kiện sai sẽ thực hiện exIfFalse. Sai ở đây có thể là null, NaN, 0, string rỗng, undefined.
  - Chuỗi điều kiện, tương tự như if-else if , syntax:
    ```javascript
    Condition1 ? exIfTrue
    : condition2 ? exIfTrue
    : condition3 ? exIfTrue
    //...
    : conditionN ? exIfTrue : exIfFalse.
    ```

## 5. Data Types

### Là các kiểu dữ liệu trong js, các biến trong js có rất nhiều kiểu giá trị

- Khái niệm kiểu dữ liệu rất quan trọng trong lập trình, nó giúp ta chỉ ra rõ với mỗi kiểu dữ liệu này, ta được phép thực hiện những công việc nào với nó, như kiểu số để tính toán, kiểu chuỗi để lưu trữ đoạn kí tự,…
- Trong js nó sẽ tự định kiểu cho biến, nếu :

  ```javascript
  let x = 16;
  //x sẽ là kiểu số tự nhiên int.
  let x = 16.5;
  //x sẽ là kiểu số nhưng là float, số thực.
  //còn nếu
  let x = “16”; //x sẽ là kiểu chuỗi ký tự String.
  ```

- Nguyên tắc định kiểu là, 2 giá trị phải cùng kiểu thì mới có thể thao tác được với nhau, js tự chuyển 2 giá trị về cùng kiểu để có thể thao tác với nhau và ước lượng kiểu dữ liệu theo thứ tự từ trái qua phải, ví dụ:

```javascript
let x = 16 + 4 “hello”;
//16 và 4 sẽ là number và cộng lại sẽ là 20, kiểu của 20 là Number
//khi cộng với chuỗi “hello” thì 20 sẽ trở thành kiểu string, //kết quả cuối cùng là 20hello.
//Ngược lại
let x = “hello” + 16 + 4
//kết quả là hello164
//“hello” là string khi cộng với 16, 16 sẽ chuyển thành string, x sẽ là kiểu string
//string cộng với 4 thì 4 sẽ chuyển thành string
```

- Một biến trong JS có thể là nhiều kiểu giá trị.
- String có thể được định nghĩa trong dấu `“ ”` hoặc `‘ ’`.
- Number có thể viết dấu `.` hoặc ko cần dấu chấm cũng được, với số cực lớn có thể dùng `e`, ví dụ:
  ```javascript
  let x = 123e5; //12300000
  let x = 123e-5; // 0.00123
  ```
- Boolean, kiểu đúng hay sai có 2 giá trị duy nhất là true, false.
- Mảng, dùng để lưu một hoặc nhiều giá trị một lúc và được biểu diễn trong dấu ngoặc [ ];
  - Các giá trị trong mảng truy cập qua index, vị trí của giá trị trong mảng, bắt đầu từ vị trí thứ 0 cho tới vị trí cuối cùng n-1.
  - Trong mảng có thể lưu trữ nhiều kiểu dữ liệu khác nhau
- Object cũng giống mảng, cũng để lưu nhiều giá trị một lúc, nhưng với object các giá trị được biểu diễn trong dấu ngoặc { }.
  - Các giá trị trong object được lưu dưới dạng key : value, các key là các property của một object, và ta truy cập vào các giá trị trong object qua các property
  - Tương tự với mảng, trong object cũng có thể lưu trữ nhiều kiểu dữ liệu khác nhau nhưng object có kiểu là object.
- Function, function là một kiểu dữ liệu trong js, điều đó có nghĩa là ta có thể gán một function cho một biến,
  ```javascript
  const x = function (variable) {
    /* do something */
  };
  //Thực thi
  x(value);
  ```
- Kiểu `undefined`, khi một biến được khởi tạo nhưng chưa được gán giá trị, biến đó sẽ có giá trị rỗng, kiểu dữ liệu là `undefined`.
- `Null`, là không tồn tại, nhưng với js `null` có kiểu là `object`.
- `Null` và `undefined` và `0`:
  - `Null` là không tồn tại, kiểu là `object`
  - `Undefined` là không có gì, kiểu là `undefined`
  - Còn `0` là có giá trị và giá trị đó bằng `0`.
- **_Immutable/ mutable_**, **_pass by value/reference_**:
  - **_Mutable_** là hành động mà giá trị của biến được lưu trong ô nhớ bị thay đổi mỗi khi ta biến đổi giá trị của biến đó như phép cộng hay trừ.
  - **_Immutable_** là hành động mà giá trị của biến được lưu trong ô nhớ không bị thay đổi mỗi khi ta biến đổi giá trị của biến đó như phép cộng hay trừ mà biến đó được gián tới một địa chỉ ô nhớ khác còn giá trị trước của nó vẫn được giữ nguyên trong ô nhớ trước đó.
  - Các kiểu dữ liệu nguyên thủy trong js đều là **_immutable_**.
- **_Pass by value_** và _**pass by reference**_:
  - **_Pass by value_**: là khi thay đổi biến trong hàm thì ngoài hàm sẽ không ảnh hưởng, tức là nó truyền giá trị và khi sử dụng các phép tính thì giá trị sẽ được lưu vào ô nhớ khác
  - **_Pass by reference_** là khi thay đổi biến trong hàm thì ngoài hàm sẽ bị ảnh hưởng, tức là nó truyền địa chỉ của ô nhớ và khi sử dụng các phép tính thì giá trị của ô nhớ sẽ bị thay đổi.
  - Trong js, khi truyền vào tham số cho hàm, giá trị của biến ở ngoài hàm không thay đổi ngay cả khi trong hàm ta gán hay thay đổi biến đó.
  - Còn với `object` việc gán cũng có kết quả tương tự, nhưng với các giá trị lưu trữ bên trong `object` được thay đổi, giá trị bên ngoài cũng thay đổi.
  - Với `const` việc gán lại giá trị cho biến sẽ không thể thực hiện còn thay đổi dữ liệu nằm trong, vs `array` và `object` thay đổi dữ liệu bên trong là có thể với `const`, const chỉ dùng để chống việc gán lại để `object` là duy nhất trong phạm vi toàn cục.

## 6. `This`, `call`, `apply`, `bind`

### `This`

- Là từ khóa để tham chiếu tới `object` bao hàm nó, cụ thể:
- Trong các phương thức, `this` trỏ tới `object` mà chứa phương thức đó.
- Từ khóa this không nằm trong `object` nào thì luôn trỏ tới `object` toàn cục.
- `Object` toàn cục bao gồm tất cả các `function`, nên trong phạm vi `function` thì this trỏ tới `object` toàn cục.
- Nhưng với `strict mode`, this trong `function` thì là undefined.
- Với sự kiện thì `this` trỏ tới element mà nhận `event`.
- Các phương thức `call( )`, `apply( )`, dung để gán `this` với `object` bất kỳ.
- Với `this` trong `callback`, `this` sẽ không được trỏ tới `this` trong đối tượng sở hữu phương thức đó, mà được gán bằng đối tượng mà nó được gọi
- Với `this` trong `closure`, `this` không tham chiếu tới `this` của hàm bên ngoài vì nó chỉ tham chiếu tới `this` của chính hàm mà nó được sử dụng mà thôi, và khi không có tham chiếu cụ thể, `this` sẽ được gán cho `object` toàn cục và `undefined` trong `strict mode`. Ta có thể gán `this` cho một biến ở hàm bên ngoài, như vậy trong `closure` có thể truy cập tới giá trị của `this`.

### Call, bind, apply

- Là các phương thức để gán `object` cho `this`:
- `Call` và `apply` sẽ gán `object` cho `this` và chạy `function` luôn khi gọi:
- `Call` truyền vào các tham số, cách nhau bởi dấu phẩy.
- `Apply` truyền vào các tham số thông qua mảng.
- `Bind` sẽ trả về một `function` mới với `this` được tham chiếu bằng `object` mà ta chỉ định và các tham số cách nhau bởi dấu phẩy.

## 7. `setTimeout`, `setInterval`

### `setTimeout`/ `clearTimeout`:

- `setTimeout` thực hiện hành động một lần sau một khoảng thời gian
- `clearTimeout` dừng việc thực hiện hàm `setTimeout`

### `setInterval`/ `clearInterval`:

- `setInterval` thực hiện một hành động nhiều lần sau một khoảng thời gian
- `clearTimeout` dừng việc thực hiện hàm `setInterval`
- `setInterval` sẽ không có độ trễ giữa 2 lời gọi hành động liên tiếp.

## 8. `Cookie`

- `Cookie` là một chuỗi nhỏ, lưu trữ những dữ liệu được lưu trực tiếp tại browser, nó là một phần của giao thức `http`.
- `Cookie` thường được tạo bởi web-server qua `response` từ `Set-Cookie` `HTTP-header`, sau đó browser sẽ tự động thêm chúng vào hầu hết mọi `req` tới cùng domain bằng `HTTP-header`.
- `Cookie` có giới hạn lưu trữ `4KB`, mỗi một `domain` chỉ có thể lưu tối đa vào khoảng 20+ `cookie`, có thời gian tồn tại sau khi hết thời gian tồn tại thì trình duyệt sẽ tự động xóa `cookie`
- Một ví dụ phổ biến nhất của `cookie` là trong việc đinh danh, xác thực tài khoản :
  - Khi đăng nhập, `server` dùng `Set-Cookie` `HTTP-header` trong `response` để tạo cookie với một định danh duy nhất, `session identifier`.
  - Khi lần `req` tiếp theo tới cùng `domain` đó, trình duyệt gửi kèm `cookie` qua `setCookie` `HTTP-header` lên `server`
  - Từ đó mà `server` biết được ai gửi `req` đó.
- Ở trình duyệt cũng có thể truy cập và chỉnh sửa `cookie` dùng thuộc tính `document.cookie`.
- Khi dùng `document.cookie` sẽ trả về một chuỗi gồm các cookie, triển khai theo cặp `name=value` được cách nhau bởi dấu `;`, mỗi một cặp là một `cookie`. Ta có thể tách chuỗi để lấy các cặp `name` `value` đó.
- `document.cookie` là hàm `setter`/`getter`, ta có thể dùng nó để lấy và ghi dữ liệu, nhưng khi chạy, hàm này cũng rất đặc biệt, nó chỉ update những `cookie` được ta đề cập mà không ghi đè hay tác động tới những `cookie` khác.
- `Cookie` có thể là bất kỳ ký tự nào, nhưng để theo một định dạng phù hợp thì ta nên dùng hàm dựng sẵn `encodeURIComponent` để chuyển đổi `name` và `value` về các ”dãy thoát”. Trái với `encodeURI` thì ta có hàm chuyển “dãy thoát” về chuỗi thường là `decodeURIComponent`.
- Các `option` của `cookie`:
  - `path=/mypath`, là đường dẫn tuyệt đối, chỉ ra những trang nào trong `domain` có thể truy cập `cookie` này, với `path=/` là toàn bộ các trang trong `domain` đều có thể truy cập
  - `domain=site.com`, là địa chỉ mà `cookie` được gửi tới cũng như được nhận và truy cập,
    - Mặc định là địa chỉ `URL` của tài liệu hiện tại nếu bị bỏ qua, không để có nhiều giá trị trong `domain`
    - Nhưng nếu `option` này được chỉ rõ thì các `subdomain` cũng có thể dùng `cookie` này.
  - `expires` và `max-age`: thời gian mà `cookie` sống
    - Nếu không có `option` này thì `cookie` sẽ là `sessionCookie`, khi trình duyệt đóng nó sẽ bị xóa
    - `expires` là thời gian dạng `date`, ví dụ`expires=Tue, 19 Jan 2038 03:14:07 GMT`
    - `max-age` là thời gian dạng giây, ví dụ `max-age=5000`
  - `secure`, nếu `option` này được khai báo thì `cookie` chỉ được truyền trong môi trường `HTTPS`, nếu bỏ qua `option` này thì `cookie` có thể được truy cập ở cả `HTTP` và `HTTPS`.
  - `samesite`, cho phép các trang khác truy cập vào `cookie` hay không
    - `samesite=strict`,
    - `samesite=lax`,
    - `samesite=none`,
  - `httpOnly`, ngăn code js truy cập vào `cookies`.
- Các hàm thao tác với cookie:
  - `getCookie(name);` đã tích hợp decode
  - `setCookie(name, value, options);` `options` là một `object` gồm các cặp `property : value`
  - `deleteCookie(name);` thay đổi giá trị `max-age` của `cookie` về -1.
- Theo luật EU (GDPR), mọi web-site phải được sự đồng ý của người dùng nếu muốn được theo dõi, phân quyền, định danh.
  - Nếu một web-site muốn dùng cookie để tracking người dùng được phân quyền, ở form đăng ký tài khoản phải có mục check-box người dùng phải chấp nhận các chính sách bảo mật, trong đó đề cập cookie sẽ được dùng ra sao, phải được có sự đồng ý của user thì web-site mới được sử dụng cookie để phân quyền
  - Nếu một web-site muốn dùng cookies để tracking tất cả mọi người truy cập vào web-site thì với người mới vào lần đầu trang web phải có cửa sổ pop-up, buộc người dùng phải click vào chấp nhận cho trang web sử dụng tracking cookies thì mới được xem các nội dung trong trang web.

## 9. Local Storage, session Storage:

### Local storage:

- Lưu trữ ở phía client, không gửi lên server do vậy không gian lưu trữ lớn hơn cookie, từ `2MB` tối thiểu cho tới `5MB` với mọi trình duyệt
- Có thời gian lưu trữ vô thời hạn, không thể xóa, chỉnh sửa bởi server qua HTTP headers, chỉ có thể chỉnh sửa bởi js.
- Mỗi `localStorage` được gán với một nguồn riêng(`domain`/`protocol`/`port triplet`), điều này có nghĩa là với các `protocol` hay `subdomain` không thể truy cập storage của nhau.
- Xử lý nó như một object, các giá trị được lưu dưới dạng `key`, `value` và chỉ dùng kiểu string cho cả 2
- Các hàm `localStorage.setItem(‘key’, ‘value’)`, `.getItem(‘key’)`, `.length()`, `.clear()`

### Session Storage:

- Giống local storage, các hàm cũng như nhau, nhưng ít được sử dụng hơn, thời gian sống trong trình duyệt tab, mất khi đóng tab, refresh lại page ko ảnh hưởng, 2 page giống nhau được mở trên 2 tab khác nhau có session storage khác nhau.

## 10. DOM/DOM:

### `DOM` (Document Object Model):

- Là mô hình lưu trữ tất cả nội dung trong một trang dưới dạng các `object` có thể chỉnh sửa.
- `DOM tree`: phần xương sống của một tài liệu `HTML` là các thẻ, mỗi một thẻ trong cây `DOM` là một đối tượng, các thẻ được gói lại sẽ là thẻ con của thẻ bao ngoài nó.
- Tất cả các đối tượng này đều có thể được truy cập bằng js cho nên ta có thể chỉnh sửa chúng.
- Trình duyệt sẽ tự động sửa lỗi cú pháp HTML khi tạo cây DOM
- Tất cả mọi thứ trong tài liệu HTML, kể cả comment, đều là một phần trong DOM.
- Mọi hoạt động trong DOM đều bắt đầu với đối tượng `document`, đó là điểm truy cập chính vào `DOM`, qua đó ta mới có thể truy cập tới các node trong `DOM`.

### `BOM` (Browser Object Model):

- Là mô hình lưu trữ các object bổ sung bởi trình duyệt tạo môi trường làm việc với các yếu tố khác ngoài tài liệu html.

## 11. `Callback`

- Là một `function` được truyền vào một `function` khác như là một tham số, `function` đó có thể chạy `callback` trong một thời gian nhất định.
- Nếu thực thi ngay lập tức thì được gọi là `synchronous callback`
- Nếu thực thi một lúc nào đó trong tương lai thì được gọi là `asynchronous callback`
