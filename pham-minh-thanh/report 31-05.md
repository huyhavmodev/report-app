# **_PROJECT CMS_***

- Migrate code Javascript to Typescript

# **_Prepare For Interview_**

+ rabbit MQ
-   RabbitMQ là một message-queuing software có thể được biết đến như là một người vận chuyển message trung gian hoặc một người quản lí các queue. Nói một cách đơn giản, nó là một phần mềm nơi các queue được định nghĩa, phục vụ cho ứng dụng với mục đích vận chuyển một hoặc nhiều message.

- Producer: Ứng dụng gửi message.
- Consumer: Ứng dụng nhận message.
- Queue: Lưu trữ messages.
- Message: Thông tin truyền từ Producer đến Consumer qua RabbitMQ.
- Connection: Một kết nối TCP giữa ứng dụng và RabbitMQ broker.
- Channel: Một kết nối ảo trong một Connection. Việc publishing hoặc consuming từ một queue đều được thực hiện trên channel.
- Exchange: Là nơi nhận message được publish từ Producer và đẩy chúng vào queue dựa vào quy tắc của từng loại Exchange. Để nhận được message, queue phải được nằm trong ít nhất 1 Exchange.
- Binding: Đảm nhận nhiệm vụ liên kết giữa Exchange và Queue.
- Routing key: Một key mà Exchange dựa vào đó để quyết định cách để định tuyến message đến queue. Có thể hiểu nôm na, Routing key là địa chỉ dành cho message.
- AMQP: Giao thức Advance Message Queuing Protocol, là giao thức truyền message trong RabbitMQ.
- User: Để có thể truy cập vào RabbitMQ, chúng ta phải có username và password. Trong RabbitMQ, mỗi user được chỉ định với một quyền hạn nào đó. User có thể được phân quyền đặc biệt cho một Vhost nào đó.
- Virtual host/Vhost: Cung cấp những cách riêng biệt để các ứng dụng dùng chung một RabbitMQ instance. Những user khác nhau có thể có các quyền khác nhau đối với vhost khác nhau. Queue và Exchange có thể được tạo, vì vậy chúng chỉ tồn tại trong một vhost.

<Ảnh minh họa>

- Các loại Exchange
+ Direct Exchange: Direct Exchange vận chuyển message đến queue dựa vào routing key. 
- Một queue được ràng buộc với một direct exchange bởi một routing key K.
- Khi có một message mới với routing key R đến direct exchange. Message sẽ được chuyển tới queue đó nếu R=K.

<Ảnh minh họa>

+ Default Exchange: Mỗi một exchange đều được đặt một tên không trùng nhau, default exchange bản chất là một direct exchange nhưng không có tên (string rỗng). Nó có một thuộc tính đặc biệt làm cho nó rất hữu ích cho các ứng dụng đơn giản: mọi queue được tạo sẽ tự động được liên kết với nó bằng một routing key giống như tên queue.

+ Fanout Exchange: Fanout exchange định tuyến message tới tất cả queue mà nó bao quanh, routing key bị bỏ qua. khi một message mới published, exchange sẽ vận chuyển message đó tới tất cả N queues. Fanout exchange được sử dụng cho định tuyến thông điệp broadcast - quảng bá.

+ Topic Exchange:
-  Topic exchange định tuyến message tới một hoặc nhiều queue dựa trên sự trùng khớp giữa routing key và pattern. Topic exchange thường sử dụng để thực hiện định tuyến thông điệp multicast.

- Phân phối dữ liệu liên quan đến vị trí địa lý cụ thể.
- Xử lý tác vụ nền được thực hiện bởi nhiều workers, mỗi công việc có khả năng xử lý các nhóm tác vụ cụ thể.
- Cập nhật tin tức liên quan đến phân loại hoặc gắn thẻ (ví dụ: chỉ dành cho một môn thể thao hoặc đội cụ thể).
- Điều phối các dịch vụ của các loại khác nhau trong cloud

+ Headers Exchange: Header exchange được thiết kế để định tuyến với nhiều thuộc tính, đễ dàng thực hiện dưới dạng tiêu đề của message hơn là routing key. Header exchange bỏ đi routing key mà thay vào đó định tuyến dựa trên header của message. Trường hợp này, broker cần một hoặc nhiều thông tin từ application developer, cụ thể là, nên quan tâm đến những tin nhắn với tiêu đề nào phù hợp hoặc tất cả chúng.

+ message queue: là một hộp thư, cho phép các thành phần/service trong một hệ thống (hoặc nhiều hệ thống), gửi thông tin cho nhau. Cơ chế FIFO – First In First Out
  - Message: Thông tin được gửi đi (có thể là text, binary hoặc JSON)
  - Message Queue: Nơi chứa những message này, cho phép producer và consumer có thể trao đổi với nhau
  - Producer: Chương trình/service tạo ra thông tin, đưa thông tin vào message queue
  - Consumer: Chương trình/service nhận message từ message queue và xử lý
  Một chương trình/service có thể vừa là producer, vừa là consumer 

+ database: mongo mysql
  - MongoDB: NoSQL
  - Mysql: SQL
+ Nodejs microservices
+ nodeJS
+ NetJS