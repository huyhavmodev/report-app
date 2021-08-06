**Array**
    Arrays dùng để lưu trữ nhiều giá trị trong một biến và có thể truy cập các giá trị đó thông qua Index.
```js
    const cars = ["Toyota", "BMW", "Honda"];
```

**Multidimensional Arrays**
    Là một tập hợp các array nằm trong một array.
```js
    const arr = [[1,2,3], [4,5,6]];
```
**Access and Iterate Through an Array**
    Chúng ta có thể sử dụng vòng lặp để truy cập đến các giá trị được lưu trong array. Ngoài ra còn có forEach() cũng dùng để truy cập và gọi ra một function(callbakc function) cho từng giá trị được lưu trong array.
```js
    const arr = [1,2,3,4,5];
    function sum(value, index, array){
        let total += value;
    }
    arr.forEach(sum);
    // => 15
```
    Ngoài forEach còn có rất nhiều các method khác có thể tương tác với Array như map(), reduce(), filter(),...

**Bubbling and capturing**
    Bubbling là khi một event xảy ra trên một element, đầu tiên nó sẽ chạy handlers trên nó, sau đấy rồi sẽ đến thẻ cha của nó, rồi lần lượt cho tới khi đến document object.

```js
<style>
  body * {
    margin: 10px;
    border: 1px solid blue;
  }
</style>

<form onclick="alert('form')">FORM
  <div onclick="alert('div')">DIV
    <p onclick="alert('p')">P</p>
  </div>
</form> 
```
    Trong ví dụ trên, các ô pop-up sẽ hiện lần lượt từ p => div => form.

    Khi một event được chạy trên một element mà có element cha, browser sẽ hoạt động qua 3 giai đoạn.
        Capturing: 
        - Trình duyệt sẽ check xem element ở ngoài cùng (<html>) có event nào được gán vào cho Capturing phase không, và sẽ chạy nó nếu có.
        - Sau đó sẽ chuyển tới element tiếp theo, và lặp lại tương tự cho tới khi đến được element cha của element được chọn.

        Target:
        - Trình duyệt sẽ kiểm tra xem target property có event nào được gán không và chạy nó.
        - Nếu như bubble là true, nó sẽ kéo theo toàn bộ event chạy ngược ra cho đến element ngoài cùng (<html>). Nếu không thì sẽ không kéo theo bất kỳ sự kiện nào cả.

        Bubbling: 
        - Trình duyệt sẽ check xem element cha của element được chọn có event nào được gán vào cho Bubbling phase không, và sẽ chạy nó nếu có.
        - Sau đó sẽ chuyển tới element tiếp theo, và lặp lại tương tự cho tới khi đến được element ngoài cùng (<html>).

        Hiện nay các trình duyệt đều mặt định tất cả các event đều được gán cho bubbling phase.

**Regular Expressions**
    Là những patterns giúp lập trình viên match, search và replace text.
```js
    let myString = "Hello, World!";
    let myRegex = /Hello/;
    let result = myString.test(myregex);
    // => true
```