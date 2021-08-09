## TRAN DAI MINH 08-04

## TOPIC: Array, Linked list, Queue, Stack, Hash table, Set, Tree, Graph, git.

- **Array** là một cấu trúc với kích thước cố định, có thể giữ các item có dùng kiểu dữ liệu.

```js
const arr = [1, 2, 3, 4, 5];
// 5 phần tử: 1, 2, 3, 4, 5
// index: có 4 index. arr[0] -> arr[4]
```

- **Linked list (Danh sách liên kết)** là một chuỗi các cấu trúc dữ liệu, với mỗi node bao gồm hai phần thông tin: dữ liệu của node và tham chiếu đến node kế tiếp trong chuỗi. Các phương thức:
  - size: Trả về số lượng các node trong list.
  - head: Trả về phần tử đầu.
  - add: Thêm một node mới ở đuôi.
  - remove: Xoá một node bất kỳ.
  - indexOf: Trả về vị trí của một node.
  - elementAt: Trả node về vị trí của nó.
  - addAt: Insert node vào một vị trí đặc biệt cụ thể.
  - removeAt: Xoá node tại vị trí đặc biệt cụ thể.
- **Queue (hàng đợi)** là một cấu trúc dạng FIFO (First In First Out - vào trước ra trước). Các phương thức:
  - Enqueue: Thêm phần tử vào cuối hàng đợi.
  - Dequeue: Xoá phần tử đầu tiên của hàng đợi.
  - Front: Trả về phần tử đầu tiên.
  - isEmpty: Xác định xem hàng đợi có đang rỗng không.
  - Size: Lấy số phần tử trong hàng đợi.
- **Stack (ngăn xếp)** là một cấu trúc dạng LIFO (Last In First Out - phần tử được đưa vào sau cùng sẽ có thể được truy cập đầu tiên). Các phương thức phổ biến:
  - push thêm phần tử mới.
  - pop lấy phần tử ở vị trí trên cùng và trả lại giá trị của phần tử đó.
  - peek trả lại phần tử phía trên cùng.
  - length trả về số lượng phần tử.
- **Hash table** là cấu trúc giữ liệu mà mỗi phần tử trong bảm băm là một cặp key-value (khoá - giá trị). Các phương thức:
  - add: Thêm một cặp key - value (khoá - giá trị).
  - remove: Xoá một cặp key - value (khoá - giá trị).
  - lookup: Sử dụng khoá để tìm giá trị tương ứng.
- **Set (Tập hợp)** là một khái niệm cơ bản trong toán học: một tập hợp các đối tượng được xác định rõ ràng và khác biệt (không trùng lặp). Các phương thức:
  - values: Trả về tất cả các phần tử trong một tập hợp.
  - size: Trả về số lượng phần tử trong một tập hợp.
  - has: Xác định xem phần tử có tồn tại không.
  - add: Chèn các phần tử vào tập hợp.
  - remove: Xoá các phần tử trong một tập hợp.
  - union: Xác định giao điểm giữa hai tập hợp.
  - difference: Trả về sự khác biệt giữa hai tập hợp.
  - subset: Xác định xem một tập hợp này có phải là con thuộc tập hợp khác không.
- **Tree** là một dạng cấu trúc nhiều tầng (multi-layer), đồng thời cũng là một dạng cấu trúc dữ liệu phi tuyến tính, so với Array (mảng), Stack (ngăn xếp) và Queue (hàng đợi). Một sô khái niệm:

  - root: Node gốc của cây, node gốc là node duy nhất không có bất kỳ node cha nào.
  - parent node: Node trực tiếp của lớp layer trên, chỉ có một.
  - child node: Các node trực tiếp của các lớp layer dưới, có thể có nhiều.
  - siblings: Chia sẻ cùng một node cha.
  - leaf (Lá): Là node không có bất kỳ node con nào.
  - Edge (Cạnh): Liên kết giữa các node.
  - Path (Đường): Đoạn dãy tập hợp các cạnh tính từ phần node đầu tiên đến node đích.
  - Height of Node (chiều cao của node): Số các cạnh theo đường dài nhất tính từ node đó đến node lá.
  - Height of Tree (chiều cao của cây): Số cạnh theo đường dài nhất tính từ node gốc đến node lá.
  - Depth of Node (độ sâu của node): Tập hợp số cạnh từ node gốc đến node đang tính.
  - Degree of Node: Số lượng các node con.

- Các phương thức:
  - add: Chèn một node vào trong một cây
  - findMin: Tìm kiếm node nhỏ nhất.
  - findMax: Tìm kiếm node lớn nhất.
  - find: Tìm kiếm một phần tử node cụ thể.
  - isPresent: Xác định sự tồn tại của một node cụ thể.
  - remove: Xoá node khỏi cây.
- **Graph** là một tập hợp các node với các liên kết. Graph được sử dụng khá rộng rãi và phổ biến, ví dụ như dùng để tính toán các tuyến đường tốt nhất trong các app về điều hướng, hay gợi ý bạn bè trên các mạng xã hội. Có 2 hướng trình bày:
  - Adjacency List (Danh sách kề): à danh sách biểu diễn tất cả các cạnh hoặc cung trong một đồ thị. Trong phương pháp này, chúng ta sẽ liệt kê tất cả các node có thể ở bên trái và hiển thị các node kết nối ở bên phải.
  - Adjacency Matrix (Ma trận kề): Ma trận kề sẽ cho hiển thị các node trong hàng và cột, các giao điểm của hàng và cột diễn giải mối quan hệ giữa các node, 0 nghĩa là không được liên kết, 1 nghĩa là liên kết, > 1 nghĩa là có trọng số khác nhau. Để truy vấn các node trong đồ thị, phải tìm kiếm toàn bộ tree network theo phương pháp Breath-First-Search (BFS) - Tìm kiếm theo chiều rộng và phướng pháp Depth-First-Search (DFS) - tìm kiếm theo chiều sâu.
