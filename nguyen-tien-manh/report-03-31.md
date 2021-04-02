# Nguyen Tien Manh - 03/31

## TOPIC: Một số sự khác biệt giữa fetch và axios

- Cú pháp cơ bản
    - Axios tốt hơn bởi vì tự động chuyển đổi dữ liệu trả về (response) tới JSON, vì vậy khi sử dụng Axios chúng ta có thể bỏ qua bước chuyển đổi dữ liệu trả về (response) tới JSON.
    - fetch() sẽ cần phải có bước chuyển đổi response sang JSON.
- Tương thích trình duyệt
    - Một trong nhiều lý do các lập trình viên ưu tiên Axios hơn Fetch là vì Axios được hỗ trợ trên nhiều trình duyệt và phiên bản chính.
    - fetch nó chỉ hỗ trợ trong Chrome 42+, Firefox 39+, Edge 14+, and Safari 10.1+.
- Handle error
    - fetch sẽ không báo lỗi nếu yêu cầu trả về mã trạng thái 400 hoặc 500, cần phải viêt logic thêm để handle error
    - Axios sẽ reject tất cả các promise của request nếu một trong các mã lỗi trên được trả về.
- Timeout
    - Để set timeout cho axios ta chỉ việc thêm tham số timeout vào trong options.
    
    ```javascript
    axios({
    method: 'post',
    url: '/login',
    timeout: 4000,    // 4 seconds timeout
    data: {
        name: "trungnguyen"
    }
    })
    .then(response => {/* handle the response */})
    .catch(error => console.error('timeout exceeded'))
    ```

    - Với fetch thì không đơn giản như thế, để set timeout trên fetch ta cần thông qua 1 thằng gọi là AbortController

    ```javascript
    const controller = new AbortController();

    const options = {
    method: 'POST',
    signal: controller.signal,
    body: JSON.stringify({
        name: 'trungnguyen',
    })
    };  
    const promise = fetch('/login', options);
    const timeoutId = setTimeout(() => controller.abort(), 4000);

    promise
    .then(response => {/* handle the response */})
    .catch(error => console.error('timeout exceeded'));
    ```

=> Đối với dự án lớn thì người ta sẽ ưa chuộng dùng axios hơn.


