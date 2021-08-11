
**ES6: scope, arrow function, template string, destructuring, default parameter, rest, spread,...**

**scope** : Trong ES6, let và const được giới thiệu để nhất quán của block scope;
    
    -- nếu var : 
```js 
            var name = 'Luke';

                if (true) {  
                var name = 'Phil';
                console.log(name); // 'Phil'
                }
                console.log(name); // 'Phil'  
```
    -- thì let sẽ chặt chẽ hơn: 
```js
                let name = 'Luke';

            if (true) {  
            let name = 'Phil';
            console.log(name); // 'Phil'
            }
            console.log(name); // 'Luke'  
```

**arrow function**  : là cách ngắn gọn hơn dùng để viết function. Ở đây sử dụng kí tự => . Arrow function là một hàm vô danh và nó thay đổi cách this bind đến function. Arrow function ngắn gọn hơn, giúp đơn giản hóa function scoping cũng như từ khóa this. Bằng cách sử dụng arrow function, chúng ta tránh được việc phải gõ từ khoá function, return và dấu ngoặc nhọn.

```js
            //ES5
                    var multiply = function(x, y) {
                return x * y;
            }; 
            
            // ES6 
            var multiply = (x, y) => { return x * y };
```
        -- TRONG TRƯỜNG HỢP LÀ 1 THAM SỐ : 
```js 
            //ES5 
            var phraseSplitterEs5 = function phraseSplitter(phrase) { 
                return phrase.split(' '); 
            }; 
            
            //ES6 
            var phraseSplitterEs6 = phrase => phrase.split(" "); 
            
            console.log(phraseSplitterEs6("ES6 Awesomeness"));  // ["ES6", "Awesomeness"]
```

        -- TRONG TRƯỜNG HỢP KHÔNG CÓ THAM SỐ : 
```js
            //ES5 
            var docLogEs5 = function docLog() { 
                console.log(document); 
            }; 
            
            //ES6 
            var docLogEs6 = () => { console.log(document); } 
            docLogEs6(); // #document... <html> ….
```

        -- Cú pháp với Object literal: 
```js
            //ES5 
            var setNameIdsEs5 = function setNameIds(id, name) { 
                return { 
                    id: id, 
                    name: name 
                }; 
            }; 
            // ES6 
            var setNameIdsEs6 = (id, name) => ({ id: id, name: name });       
            (setNameIdsEs6 (4, "Kyle"));   // Object {id: 4, name: "Kyle"} 
```

**template string**

```js
                    var cat = {
                name: 'Mun',
                job: 'Hái cau',
                bio: 'Chơi là chính, ngủ là chủ yếu, việc thì bỏ bê',
                rating: 1,
                voice: function () {
                    return 'mimi mimi';
                },
                tags: ['màu trắng', 'lùn', 'hơi nhác'],
            };

            var markup = `
                <div class="cat">
                    <h2>${cat.name}</h2>
                    <p class="job">${cat.job}</p>
                    <p class="bio">${cat.bio}</p>
                    <p class="star">${cat.rating}*</p>
                    <p class="voice">${cat.voice()}</p>
                    <p class="tags">
                        ${cat.tags.map(tag => ` <span>${tag}</span>`)}
                    </p>
                </div>
            `;
```

        -- Tagged template là 1 tính năng của  Template String .Tính năng này cho phép chúng ta truyền một template literals vào 1 hàm tag bằng cách viết tên hàm này trước dấu back-tick bắt đầu 1 template literal. Hàm tag này được dùng để xử lý chuỗi trước khi chúng được in ra hay gán vào 1 biến khác.
```js  
            var cat = 'Mèo meo';
            var action = 'loanh quanh';
            helperFunc`${cat} đi ${action}`;
            // Tương đương với việc gọi hàm
            helperFunc(["", " đi ", " trong sân."], cat, action);
            // Hàm có dạng
            function helperFunc(strings, expressionValue) {
                // strings => ["", " đi ", " trong sân."]
                // expressionValue => cat
            }
            // Hoặc
            function helperFunc(strings, ...expressionValues) {
                // strings => ["", " đi ", " trong sân."]
                // expressionValues => [cat, action]
            }
```

**destructuring** :là một cú pháp cho phép tách dữ liệu được lưu trữ bên trong (nested) Objects hoặc Arrays (tổng quát hơn là các iterable values) và gán chúng cho các biến riêng biệt. Gồm 2 nhóm chính Object Destructuring và Array Destructuring
        -- Object Destructuring
```js
            const person = { first: 'Foo', last: 'Bar' };
            const {first, last} = person;
            console.log(first); // Foo
            console.log(last);  // Bar
```
        -- Array Destructuring : 
```js
            et characters = ['a', 'b', 'c'];
            let [d, e, f] = characters;

            console.log(d, e, f); // a b c
```
        -- String trong Array Destructuring : 
```js   
        let message = 'Hello';
        let [a, b] = message;
        let [x, y, ...z] = message;

        console.log(a, b);    // H e
        console.log(x, y, z); // H e ['l', 'l', 'o']
```
        -- Array trong Array Destructuring :
```js
            let numbers = [101, 102, 103];
            let [x, y, z] = numbers;

            console.log(x, y, z); // 101 102 103
```
        -- sets trong Array Destructuring :
```js 
        let set = new Set().add('foo').add('bar');
        let [a, b] = set;

        console.log(a, b); // foo bar
```

        -- Maps trong Array Destructuring :
```js
        let map = new Map().set('a', 1).set('b', 2);
        let [x, y] = map;

        console.log(x, y); // ["a", 1] ["b", 2]
``` 

**Default parameter**
```js
            function sayHi(name = 'there') {
            console.log("Hi " + name + '!');
            }                   //Hi there
```


**Rest** Là 1 hàm có thể gọi với số lượng tham số tùy ý.
```js
        function addList(list, ...args) {
            args.forEach((arg) => list.push(arg))
            return list;
        }
            addList([1], 2, 3); // [1, 2, 3]
```

**Spread operator** giống như Rest , dùng dấu ... để lấy các tham số.

```js 
            let arr = [3, 5, 1];
        console.log( Math.max(...arr) ); // 5
```

**NodeJS and NPM**
- NodeJS: là một nền tảng (Platform) phát triển độc lập được xây dựng ở trên Javascript Runtime của Chrome mà chúng ta có thể xây dựng được các ứng dụng mạng một cách nhanh chóng và dễ dàng mở rộng.
    + Phần Core bên dưới của Nodejs được viết hầu hết bằng C++ nên cho tốc độ xử lý và hiệu năng khá cao.
    + Nodejs tạo ra được các ứng dụng có tốc độ xử lý nhanh, realtime thời gian thực.
    + Nodejs áp dụng cho các sản phẩm có lượng truy cập lớn, cần mở rộng nhanh, cần đổi mới công nghệ, hoặc tạo ra các dự án Startup nhanh nhất có thể.
- NPM - Node Package Manager: phần mềm quản lý và phân phối các gói (package) dành cho Node.

***What's LTS (Long-term support)?**
- NodeJS LTS: là phiên bản chú trọng vào tính ổn định (stability), bảo mật (security) và tuổi thọ (lifespan). Khi một phiên bản Node.js được đưa vào LTS thì đồng nghĩa với việc sẽ không có một tính năng mới nào được cập nhật ở phiên bản đó. Thay vào đó sẽ là những thay đổi trong sửa lỗi, cập nhật bảo mật, cập nhật phiên bản npm và cải thiện hiệu năng (performance). 
- NodeJS Stable chú trọng vào cập nhật tính năng và những thay đổi mới nhất. Phiên bản này sẽ được cập nhật khoảng 2 tuần đến 1 tháng một lần. Lưu ý là phiên bản này mặc dù chú trọng cập nhật nhưng vẫn là một phiên bản Stable, không phải Beta. Do đó mức độ ổn định là đủ cho mục đích sử dụng thông thường.

**Dependencies vs devDependencies vs peerDependencies**
- Dependencies: những module được dùng trong quá trình chạy sản phẩm thực tế.
- devDependencies: những module chỉ được dùng vào mục đích phát triển sản phẩm.
    + để chuyển từ Dependencies -> devDependencies: thêm --save-dev vào sau câu lệnh cài đặt package
- peerDependencies: 
    ├── request@2.12.0
    └─┬ some-other-library@1.2.3
      └── request@1.9.9

**package-lock.json and yarn.lock**
- package-lock.json: là file được tạo ra tự động khi sử dụng npm từ  bản ^5.x.x
    + Trong package-lock.json sẽ chỉ định rõ phiên bản, location, mã băm toàn vẹn integrity cho mỗi module và từng dependencies của nó.
    => Cài đặt của nó tạo ra sẽ luôn giống nhau cho dù bạn cài đặt vào lúc nào.
- yarn.lock: Yarn xác định chính xác duy nhất một version mà bạn đã cài vào file yarn.lock.
    + Các máy khác khi cài đặt dependencies sẽ tự động dựa vào yarn.lock để cài lại chính xác version của module mà bạn đã cài trên máy bạn đồng thời vẫn cho phép cài đặt module với range xác định trong package.json.
**API**
- API - Application Programming Interface (giao diện lập trình ứng dụng): là các phương thức, giao thức kết nối tới các các thư viện, ứng dụng khác.
- WEB API: là một phương thức dùng để cho phép các ứng dụng khác nhau có thể giao tiếp, trao đổi dữ liệu qua lại.
    + Dữ liệu được Web API trả lại thường ở dạng JSON hoặc XML thông qua giao thức HTTP hoặc HTTPS.

**HTTP Request (OPTIONS, GET, POST, PUT, PATH, DELETE)**
- HTTP: HyperText Transfer Protocol: giao thức truyền tải siêu văn bản.
    + OPTIONS: trả về phương thức HTTP mà server hỗ trợ.
    + GET: phương thức này dùng để lấy thông tin từ server sử dụng URI. Và phương thức GET chỉ nên dùng để lấy thông tin mà không có ảnh hưởng khác tới dữ liệu.
    + POST: phương thức này dùng để gửi dữ liệu từ client lên server, ví dụ: thông tin khách hàng, file,...
    + PUT: dùng để thay thế dữ liệu hiện tại trên server bằng một dữ liệu mới được tải lên (upload dữ liệu).
    + DELETE: xóa một tài nguyên định trước.
- HTTP Status Codes
    + 1xx: information Message
        Các status code này chỉ có tính chất tạm thời, client có thể không quan tâm.
    + 2xx Successful
        Khi đã xử lý thành công request của client, server trả về status dạng này:
        . 200 OK: request thành công.
        . 202 Accepted: request đã được nhận, nhưng không có kết quả nào trả về, thông báo cho client tiếp tục chờ đợi.
        . 204 No Content: request đã được xử lý nhưng không có thành phần nào được trả về.
        . 205 Reset: giống như 204 nhưng mã này còn yêu câu client reset lại document view.
        . 206 Partial Content: server chỉ gửi về một phần dữ liệu, phụ thuộc vào giá trị range header của client đã gửi.
    + 3xx Redirection
        Server thông báo cho client phải thực hiện thêm thao tác để hoàn tất request:
        . 301 Moved Permanently: tài nguyên đã được chuyển hoàn toàn tới địa chỉ Location trong HTTP response.
        . 303 See other: tài nguyên đã được chuyển tạm thời tới địa chỉ Location trong HTTP response.
        . 304 Not Modified: tài nguyên không thay đổi từ lần cuối client request, nên client có thể sử dụng đã lưu trong cache.
    + 4xx Client error
        Lỗi của client:
        . 400 Bad Request: request không đúng dạng, cú pháp.
        . 401 Unauthorized: client chưa xác thực.
        . 403 Forbidden: client không có quyền truy cập.
        . 404 Not Found: không tìm thấy tài nguyên.
        . 405 Method Not Allowed: phương thức không được server hỗ trợ.
    + 5xx Server Error
        Lỗi của server:
        . 500 Internal Server Error: có lỗi trong quá trình xử lý của server.
        . 501 Not Implemented: server không hỗ trợ chức năng client yêu cầu.
        . 503 Service Unavailable: Server bị quá tải, hoặc bị lỗi xử lý.

**Event Loop** : Là một vòng lặp vô tận, nó sẽ chuyển các yêu cầu sang Thread Pool (Bể chứa các luồng), đồng thời mỗi yêu cầu sẽ được đăng ký một hàm Callback. Khi một yêu cầu được xử lý xong, hàm Callback tương ứng sẽ được gọi thực thi.
