## Nguyen Minh Hieu - 03/29

### Topic: CallBack trong Javascript
#### 1. CallBack function là gì? 
- Callback được hiểu đơn giản là 1 hàm sẽ đc thực hiện sau khi 1 hàm khác đã thực hiện xong

- trong js, hàm là obj vì vậy 1 function có thể nhận tham số là function và có thể trả về 1 function. bất kì 1 function đc truyền vào dang tham số và đc gọi lại sau đó là callback function

#### 2. Tại sao lại cần callbacks

- Lý do rất quan trọng là bởi vì Javascript là một ngôn ngữ điều hành các sự việc,vì vậy mỗi lần thực thi thay vì chờ đợi phản hồi, Javascript vẫn sẽ tiếp tục thực thi các lệnh tiếp theo, đồng thời chờ đợi phản hồi từ các sự việc khác.

ví dụ khi không sử dụng Callback
``` javascript
function first(){
  // Simulate a code delay
  setTimeout( function(){
    console.log(1);
  }, 500 );
}
function second(){
  console.log(2);
}
first();
second();
```

#### 3. Nguyên tắc khi thực hiện Callback Function

- Tham số truyền vào phải là một function 

   - Điều này rất quan trọng bởi nếu bạn không kiểm tra giá trị mà người dùng truyền vào là một function thì bạn không thể thực thi được
- Callback Hell

   - Khi callback hell xuất hiện, logic xử lí của chương trình sẽ trở nên cực kì phức tạp và khó nắm bắt, khi có lỗi xảy ra ta rất khó để debug cũng như giải quyết.

``` javascript
p_client.open(function(err, p_client) {
   p_client.dropDatabase(function(err, done) {
      p_client.createCollection('test_custom_key', function(err, collection) {
         collection.insert({'a':1}, function(err, docs) {
            // ...
            // và nhiều callback nữa
         });
      });
   });
});
```