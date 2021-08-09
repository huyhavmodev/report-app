# NGUYỄN THÀNH LUÂN - Report 08/09:

***8 cấu trúc dữ liệu thường dùng**
- Mảng: là 1 biến đặc biệt chứa nhiều dữ liệu cùng 1 lúc.
    + Phần tử: các mục được lưu giữ trong mảng là 1 phần tử
    + Chỉ mục (index): mỗi vị trí của 1 phần tử trong mảng có 1 chỉ mục được sử dụng để nhận diện phần tử
    + Không thể thay đổi kích thước mảng trong quá trình sử dụng.
    + Có thể gây lãng phí bộ nhớ
```js
    const array = [1,2,3,4,5,6];
    // Phần tử : 6 phần tử
    // Chỉ mục (index): bắt đầu từ 0 ( array[0] = 1)
```
- Linked list (danh sách liên kết):
    + Danh sách liên kết là một cấu trúc dữ liệu bao gồm một nhóm các nút (node) tạo thành một chuỗi.
    + Mỗi nút (node) gồm dữ liệu ở nút đó và tham chiếu đến nút kế tiếp trong chuỗi.
    + Nút (node): gồm data và con trỏ next để trỏ đến node tiếp theo trong danh sách.
    + Node: điểm đầu (head), điểm cuối (tail).
        . unshift: thêm một hộp vào đầu chuỗi và set nó thành head mới của chuỗi.
        . push: thêm một hộp vào cuối chuỗi và sett nó thành tail mới của chuỗi.
        . shift: bỏ hộp đầu tiên của chuỗi.
        . pop: bỏ hộp cuối cùng của chuỗi.
```js
    class Node {
        constructor(value) {
        this.value = value;
        this.next = null;
        }
    }
    class SinglyLinkedList {
        constructor() {
        this.length = 0;
        this.head = null;
        this.tail = null;
        }
    }
```
    + Danh sách liên kết còn có dạng: danh sách liên kết kép và danh sách liên kết vòng.

- Queue (hàng đợi): là 1 hàng các phần tử xếp liền nhau.
    + Phần tử mới được thêm vào bằng cách xếp nó vào sau phần tử cuối cùng của hàng đợi.
    + Hoạt động: FIFO - phần tử được thêm vào đầu tiên cũng là phần tử được lấy ra đầu tiên.
    + enqueue(): thêm một phần tử vào cuối của Queue khi nó chưa đầy. Nếu thành công thì trả về true, ngược lại thì trả về false.
    + dequeue(): lấy ra một phần tử ở đầu của Queue khi nó không rỗng. Nếu thành công thì trả về giá trị phần tử đó, ngược lại thì trả về undefined;
    + front(): trả về giá trị của phần tử ở đầu của Queue khi nó không rỗng (phần tử đó vẫn tồn tại trong Queue).
    + rear(): trả về giá trị của phần tử ở cuối của Queue khi nó không rỗng (phần tử đó vẫn tồn tại trong Queue).
    + isEmpty(): kiểm tra xem Queue có rỗng hay không. Nếu đúng thì trả về true, ngược lại thì trả về false.
    + isFull(): kiểm tra xem Queue có đầy hay không. Nếu đúng thì trả về true, ngược lại thì trả về false.
    + clear(): xoá hết các phần tử khỏi Queue.

- Stack: như 1 chồng các phần tử.
    + Hoạt động: LIFO - phần tử được thêm vào cuối cùng sẽ được truy xuất ra đầu tiên.
    + push(): thêm phần tử vào ngăn xếp bằng cách thêm phần tử vào trên phần tử trên cùng.
    + pop(): lấy ra phần tử các ngăn xếp bằng cách lấy phần tử trên cùng

- Hash table: là một cấu trúc dữ liệu dùng để lưu theo các cặp key value.
    + Dùng hash function để tính toán tới một index, nơi lưu trữ một bucket các giá trị rồi từ đó sẽ retrieve ra value, mục tiêu là để độ phức tạp ở mức O(n)

- Tree: Cấu trúc dữ liệu cây biểu diễn các nút (node) được kết nối bởi các cạnh.

- Graph (đồ thị): là một dạng biểu diễn hình ảnh của một tập các đối tượng, trong đó các cặp đối tượng được kết nối bởi các link.
    + Các đối tượng được nối liền nhau được biểu diễn bởi các điểm được gọi là các đỉnh (vertices).
    + Các link mà kết nối các đỉnh với nhau được gọi là các cạnh (edges).

- Set : là tập hợp các giá trị không bị trùng lặp, nghĩa là trong một set không thể có hai giá trị bằng nhau.
```js
        const animals = new Set()
    set
        .add('cat')
        .add('dog')
        .add('snake')
    animals.size // 3
``` 

**Ajax and JSON**
- AJAX: Asynchronous JavaScript and XML - là 1 bộ các kỹ thuật xử lý các chức năng trên website.
```js
    const xhttp = new XMLHttpRequest(); // khởi tạo
    xhttp.onload = function() {

    }
    // Để gửi yêu cầu đến máy chủ: sử dụng open() và send()
    xhttp.open("GET", 'file.txt');
    xhttp.send();
```
- Phương thức:
    + new XMLHttpRequest(): khởi tạo 1 đối tượng new XMLHttpRequest.
    + abort(): hủy yêu cầu hiện tại.
    + getAllResponseHeaders(): trả về thông tin tiêu đề.
    + getResponseHeader(): trả về thông tin tiêu đề cụ thể.
    + open(method, url, async, user, psw): 
        method: yêu cầu GET hoặc POST.
        url: vị trí của tệp.
        async: true (không đồng bộ) or false (đồng bộ).
        user: tên người dùng tùy chọn.
        psw: mật khẩu tùy chọn.
    + send(): gửi yêu cầu đến máy chủ ( được sử dụng cho các yêu cầu GET).
    + send(string): gửi yêu cầu đến máy chủ ( được sử dụng cho các yêu cầu POST).
    + setRequestHeader(): thêm một cặp nhãn / giá trị vào tiêu đề sẽ được gửi 

- Thuộc tính của AJAX: 
    + onload: xác định 1 hàm được gọi khi nhận được yêu cầu.
    + onreadystatechange: xác định 1 hàm được gọi khi thuộc tính thay đổi.
    + readyState: giữ trạng thái của  XMLHttpRequest.
        0: yêu cầu không được khởi tạo
        1: kết nối máy chủ được thiết lập
        2: nhận được yêu cầu
        3: yêu cầu xử lý
        4: yêu cầu hoàn thành và phản hồi đã sẵn sàng
    + responseText: trả về dữ liệu dưới dạng chuỗi
    + responseXML: trả về dữ liệu dưới dạng XML
    + status: trả về trạng thái của yêu cầu.
        200: "OK"
        403: "Forbidden"
        404: "Not Found"
    + statusText: trả về văn bản dưới dạng trạng thái.

- JSON - JavaScript Object Notation: là 1 định dạng dữ liệu (chuỗi).
    + Trong JSON: các giá trị phải thuộc 1 trong các kiểu dữ liệu: string, number, boolean, array, object, null
    + Trong JSON: các giá trị chuỗi phải dùng dấu ngoặc kép ( "" ).
    + stringify(): Javascript types -> JSON.
    + parse(): JSON -> Javascript types.
```js
    // Khai báo tạo JSON
    var jsonArr = '["ReactJS", "Angular"]';
    var jsonObj = '{"id": 1, "name": "ReactJS"}';
    var obj = {
        id: 2,
        name: Angular
    };
    console.log(parse(jsonArr)); // Run => ['ReactJS', 'Angular];
    console.log(stringify(obj)); // {"id": 2, "name": "Angular"};
```

**Promise**
- Promise: là một cơ chế trong JavaScript giúp bạn thực thi các tác vụ bất đồng bộ mà không rơi vào callback hell.
    + Promise có 3 trạng thái: Pending - Fulfilled - Rejected
```js
    var myPromise = new Promise(
        function(resolve, reject) {
            // resolve(): thành công
            // reject(): thất bại
        }
    );
    myPromise
        .then( function(){
            // Chạy khi resolve
        });
        .catch( function(){
            // Chạy khi reject
        });
        .finally( function(){
            // Chạy khi resolve hoặc reject chạy
        });
```

**Async/Await syntax**
- Async/Await: là cơ chế giúp thực hiện các tác vụ bất đồng bộ tuần tự hơn.
    + Kết quả trả về của async function là 1 promise.
    + Để sử dụng khai báo hàm với từ khóa "async" và trong hàm sử dụng "await"
```js
     async function getAPI() {
        let json = await axios.get('url');

        return json;
    }
```

**Ajax request (Fetch API, Axios)**
- Fetch API: Fetch API là một API đơn giản cho việc gửi và nhận requesst bằng js. 
    + Với fetch thì việc thực hiện các yêu cầu web và xử lý phản hồi dễ dàng hơn so với XMLHttpRequest cũ.
```js
    fetch('examples/example.json')
        .then(function(response) {

    })
    .catch(function(error) {
        console.log('Looks like there was a problem: \n', error);
    });
```
- Axios: là một HTTP client được viết dựa trên Promises được dùng để hỗ trợ cho việc xây dựng các ứng dụng API từ đơn giản đến phức tạp.
    + Có thể được sử dụng cả ở trình duyệt hay Node.js.
```js
    npm i axios // install
    import axios from 'axios'; // import axios để có thể sử dụng

    const axios = require('axios');
```

**ES6**
- Scope: phạm vi hoạt động.
    + Trong ES6 thêm từ khóa khai báo biến 'let'.
```js
    {
        var fullName = "Nguyen Thanh Luan";
    }
    console.log(fullName); // Run => "Nguyen Thanh Luan"

    {
        let fullName = "Nguyen Thanh Luan";
    }
    console.log(fullName); // Run => fullName is not defined
    // let chỉ có tác dụng trong code block chưa nó hoặc các code block con bên trong nó.
```
- Arrow function:
```js
    // ES5
    function sum(a,b){
        return a+b;
    } // Declare function

    var sum = function(a,b){
        return a+b;
    } // Express function

    // ES6: Arrow function
    var sum = (a,b) => a+ b;