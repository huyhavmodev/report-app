# Lặp các phần tử của mảng.

## `forEach()`,

- chạy callback với từng phần tử của arr, syntax:
  ```javascript
  arr.forEach(function (item, index, array) {
    // ... do something with item
  });
  ```

## `for ... of`,

- Lặp qua tất cả các giá trị của mảng, tuy không biết được index của giá trị hiện tại, nhưng với 1 số case chỉ cần data trong array là đủ, syntax:
  ```javascript
  let arr = ["khanh", "linh"];
  for (let x of arr) {
    console.log(x);
  }
  //log khanh
  //log linh
  ```

## `for ... in`,

- Cũng giống như `for ... of` nhưng nó lặp qua cả những property không phải kiểu số của mảng.
  - Điều này xảy ra với những object dạng array, ngoài những property index thì nó có những property không phải kiểu số mà đôi khi ta không cần, điều này tạo ra sự dư thừa, đôi khi cũng khiến ta gặp phải những kết quả không mong muốn
  - `for ... in` tốt hơn hết chỉ nên sử dụng cho `object`nói chung, còn `for ... of` nên dùng cho array.

## `filter()`,

- Trả về một mảng các phần tử trong mảng đúng với điều kiện. Syntax:
  ```javascript
  let results = arr.filter(function (item, index, array) {
    // nếu đúng thì đẩy giá trị vào results
    // nếu không có phần tử nào thì trả về mảng rỗng
  });
  ```

## `map()`,

- Chạy function trên từng phần tử của mảng và trả về mảng kết quả, syntax:
  ```javascript
  let results = arr.map(function (item, index, array) {
    // trả về giá trị kết quả.
  });
  ```

## `reduce`, `reduceRight`,

- Trả về giá trị dựa vào các thành phần trong mảng, syntax:
  ```javascript
  let results = arr.reduce(
    function (accumulator, item, index, array) {
      // ...
    },
    [initial]
  );
  ```
  - Với `accumulator` là kết quả của lần thực hiện hàm với phần tử trước, `accumulator = initial` trong lần chạy đầu (nếu có), nếu không thì `accumulator = arr[0]`.
  - `item` là phần tử hiện tại của mảng.
  - `index` là index của item
  - `array` là mảng.
  - `reduceRight` cũng như `reduce` chỉ khác là nó chạy từ phải qua trái.
