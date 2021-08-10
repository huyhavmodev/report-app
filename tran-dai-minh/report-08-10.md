## TRAN DAI MINH 08-04

## TOPIC: Tìm hiểu nodejs, npm, LTS, Dependencies vs devDependencies vs peerDependencies, package-lock.json and yarn.lock, Event Loop, API, HTTP Request (OPTIONS, GET, POST, PUT, PATCH, DELETE), CORS issue, Authentication/Authorization, JSON web token (JWT), RESTful vs GraphQL concept.

- What is nodejs ? là một nền tảng (Platform) được xây dựng trên nền tảng Javascript V8 Engine. Được xây dựng để phát triển những ứng dụng server side. Phần core sử dụng Javascript và C++ cho phép xử lý với hiệu năng cao. Phù hợp với các ứng dụng xử lý nhanh, real time hoặc những ứng dụng cần thay đổi công nghệ nhanh. Chạy sigle thread nhưng có cơ chế non blocking giúp chạy bất đồng bộ, tăng khả năng xử lý.

- What is npm ? viết tắt của từ Node Package Manager là một công cụ tạo và quản lý các thư viện javascript cho Nodejs. NPM cung cấp 2 chức năng chính bao gồm:
  - Là kho lưu trữ trực tuyến cho các package/module. Chúng ta có thể tìm kiếm các package trên search.nodejs.org.
  - Quản lý các module javascript và phiên bản của chúng trong các dự án của chúng ta đơn giản hơn, dễ dàng hơn, tiết kiệm thời gian hơn.
- What is LTS ?

- Dependencies vs devDependencies vs peerDependencies

  - Dependencies là những thư viện mà dự án cần thực sự cần để hoạt động của project.

  - devDependencies là những thư viện mà bạn cần trong quá trình phát triển, Để thêm **devDependencies**, bạn chỉ cần thêm -D hoặc --dev tùy chọn để dòng lệnh của yarn or npm.

  - peerDependencies là thêm những version dependencies của 1 main-project dưới dạng peer-lib (--peer), nếu người khác install project đó các version khác với main-project thì sẽ có cảnh báo.

- package-lock.json and yarn.lock

  - package-lock.json được tạo tự động khi sửa đổi node_modules or package.json, nó sẽ mô tả chính xác các dependencies sao cho lần install tiếp theo giống hệt nhau, bất kể là cập nhật.

  - yarn.lock cũng giống package.json là 1 file dùng để lưu trữ chính xác các version của dependencies đã được cài đặt.

- Event Loop

- API là viết tắt của Application Programming Interface (giao diện lập trình ứng dụng) phương thức kết nối với các thư viện và ứng dụng khác.

- HTTP Request (OPTIONS, GET, POST, PUT, PATCH, DELETE)

  - GET lấy dữ liệu.
  - POST thêm dư liệu.
  - PUT update toàn bộ dư liệu.
  - PATCH update 1 phần dữ liệu.
  - DELETE xoá 1 dữ liệu.
  - OPTIONS mô tả các tuỳ chọn giao tiếp với resource.

- CORS issue là một cơ chế dựa trên HTTP - header cho phép máy chủ chỉ ra bất kỳ origin nào (domain, scheme, or port) khác với origin mà từ đó trình duyệt sẽ cho phép tải tài nguyên.

  ![cros](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/cors_principle.png)

- Authentication/Authorization

- JSON web token (JWT)

- RESTful là một tiêu chuẩn dùng trong việc thiết kế API cho các ứng dụng web (thiết kế Web services) để tiện cho việc quản lý các resource. Các thành phàn của nó:

  - API (Application Programming Interface) là một tập các quy tắc và cơ chế mà theo đó, một ứng dụng hay một thành phần sẽ tương tác với một ứng dụng hay thành phần khác. API có thể trả về dữ liệu mà bạn cần cho ứng dụng của mình ở những kiểu dữ liệu phổ biến như JSON hay XML.
  - REST (Representational state transfer) là một dạng chuyển đổi cấu trúc dữ liệu, một kiểu kiến trúc để viết API. Nó sử dụng phương thức HTTP đơn giản để tạo cho giao tiếp giữa các máy. Vì vậy, thay vì sử dụng một URL cho việc xử lý một số thông tin người dùng, REST gửi một yêu cầu HTTP như GET, POST, DELETE, vv đến một URL để xử lý dữ liệu.
  - RESTful API là một tiêu chuẩn dùng trong việc thiết kế các API cho các ứng dụng web để quản lý các resource. RESTful là một trong những kiểu thiết kế API được sử dụng phổ biến ngày nay để cho các ứng dụng (web, mobile…) khác nhau giao tiếp với nhau.

  ![rest](https://images.viblo.asia/c502a773-8ac5-4f33-bbf8-fa56916b70dc.png)

- GraphQL (Graph Query Language) là một ngôn ngữ truy vấn cho API của bạn và một thời gian chạy phía máy chủ để thực thi các truy vấn bằng cách sử dụng hệ thống mà bạn xác định cho dữ liệu của mình. GraphQL không bị ràng buộc với bất kỳ cơ sở dữ liệu hoặc công cụ lưu trữ cụ thể nào và thay vào đó được hỗ trợ bởi mã và dữ liệu hiện có của bạn. Bao gồm 3 điểm đặc trưng:
  - Cho phép client xác định chính xác những dữ liệu gì họ cần.
  - GraphQL làm cho việc tổng hợp dữ liệu từ nhiều nguồn dễ dàng hơn.
  - Sử dụng một type system để khai báo dữ liệu.
