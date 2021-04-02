Bubbling and capturing
Giả sử chúng ta gán event cho nhiều thẻ html lồng nhau (nested)
-Bubbling là quá trình khi event được kích hoạt trên phần tử, nó sẽ chạy 
handler trên nó trước, sau đó sẽ tới các phần tử cha của nó, tiếp tục đến
các ancestor.
-Capturing ngược lại với bubbling, khi kích hoạt event các phần tử ancestor sẽ 
chạy handler trước, rồi mới đến các phần tử con nằm trong nó 
-Hầu hết các event đều có sự kiện bubbling, trừ Focus/ 1 số ít event khác
-Có thể stop bubbling bằng event.stopPropagation()