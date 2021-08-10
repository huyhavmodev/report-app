## TRAN DAI MINH 08-04

## TOPIC: Tìm hiểu nodejs, npm, LTS, Dependencies vs devDependencies vs peerDependencies, package-lock.json and yarn.lock, Event Loop, API, HTTP Request (OPTIONS, GET, POST, PUT, PATH, DELETE), CORS issue, Authentication/Authorization, JSON web token (JWT), RESTful vs GraphQL concept.

- What is nodejs ? là một nền tảng (Platform) được xây dựng trên nền tảng Javascript V8 Engine. Được xây dựng để phát triển những ứng dụng server side. Phần core sử dụng Javascript và C++ cho phép xử lý với hiệu năng cao. Phù hợp với các ứng dụng xử lý nhanh, real time hoặc những ứng dụng cần thay đổi công nghệ nhanh. Chạy sigle thread nhưng có cơ chế non blocking giúp chạy bất đồng bộ, tăng khả năng xử lý.

- What is npm ? viết tắt của từ Node Package Manager là một công cụ tạo và quản lý các thư viện javascript cho Nodejs. NPM cung cấp 2 chức năng chính bao gồm:
  - Là kho lưu trữ trực tuyến cho các package/module. Chúng ta có thể tìm kiếm các package trên search.nodejs.org.
  - Quản lý các module javascript và phiên bản của chúng trong các dự án của chúng ta đơn giản hơn, dễ dàng hơn, tiết kiệm thời gian hơn.
- What is LTS ?
- devDependencies vs peerDependencies

  - devDependencies là những thư viện mà bạn cần trong quá trình phát triển, Để thêm **devDependencies**, bạn chỉ cần thêm -D hoặc --dev tùy chọn để dòng lệnh của yarn or npm.

  - peerDependencies là thêm những version dependencies của 1 main-project dưới dạng peer-lib (--peer), nếu người khác install project đó các version khác với main-project thì sẽ có cảnh báo.

- package-lock.json and yarn.lock

  - package-lock.json được tạo tự động khi sửa đổi node_modules or package.json, nó sẽ mô tả chính xác các dependencies sao cho lần install tiếp theo giống hệt nhau, bất kể là cập nhật.

  - yarn.lock cũng giống package.json là 1 file dùng để lưu trữ chính xác các version của dependencies đã được cài đặt.

- Event Loop

- API là viết tắt của Application Programming Interface (giao diện lập trình ứng dụng) phương thức kết nối với các thư viện và ứng dụng khác.

- HTTP Request (OPTIONS, GET, POST, PUT, PATH, DELETE)

- CORS issue là một cơ chế dựa trên HTTP - header cho phép máy chủ chỉ ra bất kỳ origin nào (domain, scheme, or port) khác với origin mà từ đó trình duyệt sẽ cho phép tải tài nguyên.

      ![cros-01](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/cors_principle.png)

- Authentication/Authorization
- JSON web token (JWT)
- RESTful vs GraphQL concept
