**8 kiểu cấu trúc dữ liệu thường dùng:**
- Array
- Linked list
        --Với Linked list, bạn có thể dễ dàng:
            -unshift: thêm một hộp vào đầu chuỗi và set nó thành head mới của chuỗi.
            -push: thêm một hộp vào cuối chuỗi và sett nó thành tail mới của chuỗi.
            -shift: bỏ hộp đầu tiên của chuỗi.
            -pop: bỏ hộp cuối cùng của chuỗi.

- Queue : Queue là một hàng các phần tử xếp liên tiếp nhau. Một phần tử mới được enqueue/thêm vào bằng cách xêp nó vào sau phần tử cuối cùng của hàng đợi. Ngược lại, ta có thể dequeue/ bỏ phần tử bằng cách lấy đi phần tử đầu tiên của hàng đợi. Nguyên lý vận hành của queue là: phần tử được thêm vào đầu tiên cũng là phần tử được lấy ra đầu tiên (FIFO, First In First Out)

- Stack : Stack như một chồng các phần tử, phần tử này nằm lên trên phần tử khác. Ta có thể push/thêm một phần tử mới vào stack bằng cách đặt nó lên trên phần từ trên cùng của stack. Ngược lại ta cũng có thể pop/ lấy ra một phần tử của trong stack ra bằng cách lấy đi phần tử trên cùng. Phần tử được thêm vào cuối cùng, luôn là phần tử được lấy ra đầu tiên (LIFO, Last In First Out)

- Hash table : một cấu trúc dữ liệu dùng để lưu theo các cặp key value, nó dùng hash function để tính toán tới một index, nơi lưu trữ một bucket các giá trị rồi từ đó sẽ retrieve ra value, mục tiêu là để độ phức tạp ở mức O(n)

- Set : là tập hợp các giá trị không bị trùng lặp, nghĩa là trong một set không thể có hai giá trị bằng nhau.
```js
        const s = new Set()
    set
        .add('red')
        .add('blue')
        .add('sweet')
        .add('you')
    s.size // 4
```

- Tree : 
- Graph :


**AJAX và JSON** 

**AJAX** là từ viết tắt của từ Asynchronous JavaScript And XML - Bất đồng bộ trong Javascript và XML. 
```js 
var variableName = new XMLHttpRequest(); // khởi tạo ajax
``` 
        --Thuộc tính
            XMLHttpRequest Object Properties

            onreadystatechange: Xác định một hàm được gọi khi thuộc tính readyState thay đổi.
            readyState: Trạng thái của XMLHttpRequest.
                   Trong đó nếu giá trị bằng các giá trị sau thì sẽ có trạng thái tương ứng.        

                       0 - request chưa được khởi tạo.

                       1 - kết nối đến server đang được thiết lập.

                       2 - yêu cầu đã nhận được.

                       3 - đang tiến hành xử lý.

                       4 -  request đã xong và dữ liệu trả về đã sẵn sàng để xử lý.

                        responseText: Giá trị trả về dưới dạng string.
                        responseXML: Giá trị trả về dưới dạng XML.
                        status: Trả về trạng thái của request. VD: 
                                200: "OK"
                                403: "Forbidden"
                                404: "Not Found"

                        statusText: Trả về trạng thái của request dưới dạng text. VD: Ok, Not Found.

        -- Phương thức:
                XMLHttpRequest Object Methods
                new XMLHttpRequest(): Tạo đối tượng XMLHttpRequest.
                abort(): Hủy Request hiện tại.
                getAllResponseHeaders(): Lấy ra thông tin header.
                getResponseHeader(): Trả về cụ thể thông tin header.
                open(method, url, async, user, psw): Cấu hình cho một request mới.
                send(string): Gửi dữ liệu đến server đã được cấu hình ở phương thức open(). Trong đó string là data các bạn muốn truyền theo nếu request là POST.
                setRequestHeader(): Thiết lập các thông số header gửi lên.

 -- POST & GET Request trong AJAX:  
        -- GET Request thường được sử dụng để lấy hoặc truy xuất một số loại thông tin từ máy chủ mà không yêu cầy bất kì thao tác hoặc thay đổi nào trong cơ sở dữ liệu.

        -- POST Request chủ yếu được sử dụng để gửi dữ liệu biểu mẫu đến máy chủ web.

**JSON**
    -- JSON là viết tắt của Javascript Object Notation, là một bộ quy tắc về cách trình bày và mô tả dữ liệu trong một chuỗi lớn thống nhất được gọi chung là chuỗi JSON.

```JS 
    {"Name" : "Code Learn","Age" :2}
// Hoặc có thể viết lại như sau :
    { 
    "Name" : "Code Learn", 
    "Age" : 2 
    }
```
    -- Cách làm việc với JSON
            1.Dùng phương thức JSON.parse() để tạo ra object javascript:
```js
                var str='{
                    "company":"facebook",
                    "CEO":"Mark Zuckerberg",
                    "employees":[{"name": "John","age": 25},{"name": "Anna","age": 29}]
                    }';

            var obj = JSON.parse(str); // đây là object javascript được tạo từ chuỗi JSON

            /* truy cập vào thuộc tính JSON bằng tên thuộc tính */
            console.log(obj.company) ;           // facebook
            console.log(obj.employees[0].name) ; // John
            console.log(obj.employees[1].name) ; // Anna
```

    -- Dùng phương thức JSON.stringify() để tạo chuỗi JSON từ Object Javascript:

```js
            var obj = {name : "John", age : 29};
 
            var text = JSON.stringify(obj);
            
            console.log(text); // {"name":"John","age":29}
```