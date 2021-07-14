# Nguyen Huy An - 07/13

## Event Loop

- Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model), trước giờ vẫn nghe nói NodeJs có thể xử lý cả hàng ngàn request cùng một lúc mặc dù nó chỉ dùng một thread duy nhất (Single Threaded)Event Loop là cơ chế giúp Javascript có thể thực hiện nhiều thao tác cùng một lúc (concurrent model), NodeJs có thể xử lý nhiều request cùng một lúc mặc dù nó chỉ dùng một thread duy nhất (Single Threaded).

Một số khái niệm:
- Heap: Heap là vùng nhớ được dùng để chưa kết quả tạm phục vụ cho việc thực thi các hàm trong stack. Heap càng lớn thì khả năng tính toán càng cao. Heap có thể được cấp phát tĩnh hoặc cấp phát động bằng mấy lệnh kiểu alloc với malloc
- Call Stack: là 1 stack hoạt động theo kiểu hàng đợi LIFO (last in first out). 1 hàm chỉ có thể lấy ra khi nó đã hoàn thành và return
- Event Queue: là 1 queue hoạt động theo kiểu hàng đợi FIFO (first in first out). Mỗi khi có một Event được tạo ra, ví dụ user click vào một Button thì một Event sẽ được đẩy vào Event queue cùng với một handler (event listener) gắn với nó. Nếu một Event không có listener thì nó sẽ bị mất và không được đẩy vào Event queue
- Stack trace: đường đi từ hàm main đến hàm vừa gọi
- Stackoverflow: khi gọi 1 hàm đệ quy vô tận đến khi tràn bộ nhớ stack sẽ xảy ra lỗi stackoverflow

- Event Loop có nhiệm vụ rất đơn giản là đọc Call Stack và Event Queue. Nếu stack rỗng thì nó sẽ đẩy event đầu tiên của queue và handler (callback hoặc listener)

## NodeJs

- Node.js là một JavaScript runtime được build dựa trên engine JavaScript V8 của Chrome. Node.js sử dụng kiến trúc hướng sự kiện event-driven, mô hình non-blocking I/O làm cho nó nhẹ và hiệu quả hơn. Hệ thống nén của Node.js, npm, là hệ thống thư viện nguồn mở lớn nhất thế giới.

## Npm

- NMP là viết tắt của Node package manager là một công cụ tạo và quản lý các thư viện lập trình Javascript cho Node.js. Trong cộng đồng Javascript, các lập trình viên chia sẻ hàng trăm nghìn các thư viện với các đoạn code đã thực hiện sẵn một chức năng nào đó. Nó giúp cho các dự án mới tránh phải viết lại các thành phần cơ bản, các thư viện lập trình hay thậm chí cả các framework. Với npm , công việc sẽ đơn giản đi rất nhiều, chúng giúp bạn thực hiện việc quản lý đơn giản hơn rất nhiều. Các thư viện đều có sẵn trên npm, bạn chạy một dòng lệnh để tải về và dễ dàng include chúng hơn.

## LTS

- Long-Term-Support được áp dụng với các release sẽ được Node.js hỗ trợ và bảo trì trong thời gian dài

- Active: Một dòng phát hành Active LTS là một dòng đang được duy trì và nâng cấp tích cực, bao gồm việc đưa vào các tính năng, chức năng và cải tiến hơn, giải quyết các lỗi và vá các lỗ hổng bảo mật.

- Maintenance: Dòng phát hành LTS bảo trì là dòng phát hành LTS của Node.js gần End of Life (EOL) và sẽ chỉ nhận được các bản sửa lỗi và bản vá bảo mật trong một thời gian ngắn