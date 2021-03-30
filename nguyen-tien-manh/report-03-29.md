# Nguyen Tien Manh - 03/29

## TOPIC: requestAnimationFrame và cancleAnimationFrame

- Là phương thức cho trình duyệt biết bạn muốn thực hiện 1 animation và yêu cầu trình duyệt gọi một function được chỉ định để
  cập nhật animation trước lần repaint tiếp theo.
- Khi muốn thực hiện một vòng lặp time trong javascript thì có thể nghĩ đến setInterval. Tuy nhiên khi làm animation để nó chuyển động mượt mà hơn thì nên dùng requestAnimationFrame.
- Ở máy tính mình thì có thể xử lý chuyển động 60fps, tuy nhiên máy khách hàng kém hơn là 25fps.
  - Làm sao để biết các máy xử lý bao nhiêu fps để tính toán
    - setInterval (1000/60) hay setInterval (1000/25).
  - => Không biết fps máy khách nên requestAnimationFrame nó sẽ tự xác định mức fps phù hợp nhất cho người dùng.
- Animation sẽ dừng lại khi tab not active còn setInterval sẽ vẫn chạy
- Tương tự để thực hiện dừng animation thì có thể lấy giá trị trả về của requestAnimationframe để cancle animation đó.
- Demo

```php

<button id="start">start</button>
<button id="stop">stop</button>
<script type="text/javascript">
    let globalID;

    function repeatOften() {
    $("<div />").appendTo("body");
    globalID = requestAnimationFrame(repeatOften);
    }

    globalID = requestAnimationFrame(repeatOften);

    $("#stop").on("click", function () {
    cancelAnimationFrame(globalID);
    });
    
    $("#start").on("click", function () {
    globalID = requestAnimationFrame(repeatOften);
    });
</script>

```
