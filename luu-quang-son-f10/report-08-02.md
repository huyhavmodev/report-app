# DAY 1+2 :
**Hoisting?**
-- là cơ chế của JavaScript cho phép các khai báo biến hoặc hàm được dời lên trên đầu phạm vi của chúng trước khi thực thi đoạn code. ( chỉ di chuyển phần khai báo)
    - Hoisting đối với biến: 
```js     function hoi() {
        // Vừa khai báo, vừa khởi tạo
        // trước khi sử dụng
         var message = "Hoisting";
        console.log(message);
    }
    hoi(); /// Hoisting
```
    -  Hoisting đối với hàm: giống như khai báo biến.
    - Thứ tự ưu tiên trong Hoisting :
        1.Gán biến ưu tiên hơn khai báo hàm;
        2.Biểu thức hàm ưu tiên hơn gán biến;
        3.Khai báo hàm ưu tiên hơn khai báo biến


**Scope và Closure?**
-- Là phạm vi có thể sử dụng được các variable tùy ý.