**promise, async await syntax**

**Promise** một đối tượng được sử dụng cho tính toán bất đồng bộ. Một promise đại diện cho một tiến trình hay một tác vụ chưa thể hoàn thành ngay được. 
            -- resolve là hàm sẽ được gọi khi promise hoàn thành.
            -- reject là hàm sẽ được gọi khi có lỗi xảy ra.
```js
            var promise = new Promise (function a(resolve, reject) {
    if(// task complete) {
        resolve(value);
    } else {
        reject(new Error());
    }
});
```
    -- Phương thức .then() luôn được đưa vào , đòi hỏi tham số của nó phải là một hàm. Nếu bạn đưa vào .then() một giá trị, nó sẽ bị bỏ qua. 
```js
        Promise.resolve(1)
        .then(2)
        .then(console.log) // kết quả là 1.
      //  =>>>>>>>>>>> cách giải quyết là t đưa vào 1 hàm trong .then()
         Promise.resolve(1)
            .then(() => 2)
            .then(() => Promise.resolve(2))
            .then(console.log) // 2
```

        -- Phương thức .catch() để xử lý lỗi. Nó dễ đọc hơn là xử lý các lỗi bên trong .then()

```js
            const Promise = new Promise ((resolve,reject) => {
              
                });
                promise
                .then ((data) => { 
                    console.log (data); 
                }) 
                .catch ((error) => { 
                    console.log (error); // in ra Error object 
                });
```

        -- Promise.all() nhận một mảng các promise làm đầu vào và trả về một promise mới thực hiện khi tất cả các promse bên trong mảng đầu vào đã hoàn thành hoặc từ chối ngay khi một trong các promise trong mảng từ chối. 
```js
             const Promise1 = new Promise ((resolve,reject) => { 
                setTimeout (() => { 
                resolve ('Promise1 đã giải quyết'); 
                }, 2000); 
                });
                const Promise2 = new Promise ((giải quyết, từ chối) => { 
                setTimeout (() => { 
                resolve ('Promise2 đã giải quyết'); 
                }, 1500); 
                });
                Promise.all ([promise1, promise2]) .then 
                ((data) => console.log (data [0], data [1])) 
                .catch ((error) => console.log (error));
```

        -- Promise.race() nhận một mảng các promise làm đầu vào và trả về một promise mới thực hiện ngay khi một trong cácpromise trong mảng đầu vào thực hiện hoặc từ chối ngay khi một trong các promise trong mảng đầu vào từ chối

```js  
        const promise1 = new Promise((resolve, reject) => {
            setTimeout(() => {
            resolve('Promise1 resolved');
            }, 1000);
            });
            const promise2 = new Promise((resolve, reject) => {
            setTimeout(() => {
            reject('Promise2 rejected');
            }, 1500);
            });
            Promise.race([promise1, promise2])
            .then((data) => console.log(data))  // Promise1 resolved
            .catch((error) => console.log(error));
```

**Async / Await** là một tính năng của JavaScript giúp chúng ta làm việc với các hàm bất đồng bộ theo cách thú vị hơn và dễ hiểu hơn. Nó được xây dựng trên Promises và tương thích với tất cả các Promise dựa trên API.
        -- Async - khai báo một hàm bất đồng bộ (async function someName(){...}).
                    Tự động biến đổi một hàm thông thường thành một Promise.
                    Khi gọi tới hàm async nó sẽ xử lý mọi thứ và được trả về kết quả trong hàm của nó.
                    Async cho phép sử dụng Await.

        -- Await - tạm dừng việc thực hiện các hàm async. (Var result = await someAsyncCall ()😉.
                    Khi được đặt trước một Promise, nó sẽ đợi cho đến khi Promise kết thúc và trả về kết quả.
                    Await chỉ làm việc với Promises, nó không hoạt động với callbacks.
                    Await chỉ có thể được sử dụng bên trong các function async.
        


**Ajax request (Fetch API, Axios)**

**Fetch API**  xây dựng một hàm fetch(url,options) dùng để lấy dữ liệu từ một URL, hàm này trả về một Promise.
```js
            var url = "http://example.com/file";
                var options = { method : 'GET', .... };
                
                var aPromise = fetch(url, options);
                
                aPromise
                    .then(function(response) {
                        
                    })
                    .catch(function(error) {
                        
                    });
```

**Axios** là một HTTP client được viết dựa trên Promises được dùng để hỗ trợ cho việc xây dựng các ứng dụng API từ đơn giản đến phức tạp và có thể được sử dụng cả ở trình duyệt hay Node.js.
    -- Tạo một request với Axios : 
```js
        axios({
            method: 'post',
            url: '/login',
            data: {
                user: 'test',
                lastName: 'test1'
            }
            });
```
        -- Các option cho Request:
            - baseURL: nếu bạn chỉ định một base URL, nó sẽ được đính vào trước bất cứ một URL tương đối nào mà bạn sử dụng.
            - headers: một object gồm các cặp key/value có thể gửi trong header của request.
            - params: một object gồm các cặp key/value mà sẽ được serialize và đính vào URL dưới dạng một query string.
            - responseType: nếu bạn mong chờ một format trả về khác ngoài JSON, thì bạn có thể set thuộc tính này thành arraybuffer, blob, document, text hay stream
            - auth: truyền vào một object gồm 2 trường username và password được sử dụng để cung cấp quyền truy cập cho các request yêu cầu HTTP Basic auth.
        
        -- Các hàm get, delete, head và options đều nhận vào 2 tham số là URL và một object option dùng để config request.
```js
        axios.post(
            '/products',
            { name: 'Waffle Iron', price: 21.50 },
            { options }
            );
```


**ES6: scope, arrow function, template string, destructuring, default parameter, rest, spread,...**

**scope**