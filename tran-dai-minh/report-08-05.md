## TRAN DAI MINH 08-05

## TOPIC: Cookie/localStorage/sessionStorage, DOM, BOM, Bubbling and capturing, Regular-expressions.

- **LocalStorage** khả năng lưu trữ vô thời hạn: Có nghĩa là chỉ bị xóa bằng JavaScript, hoặc xóa bộ nhớ trình duyệt, hoặc xóa bằng localStorage API. Lưu trữ được 5MB: Local Storage cho phép bạn lưu trữ thông tin tương đối lớn lên đến 5MB, lưu được lượng thông tin lớn nhất trong 3 loại. Không gửi thông tin lên server như Cookie nên bảo mật tốt hơn.

- **Session Storage** Lưu trên Client: Cũng giống như localStorage thì sessionStorage cũng dùng để lưu trữ dữ liệu trên trình duyệt của khách truy cập (client). Mất dữ liệu khi đóng tab: Dữ liệu của sessionStorage sẽ mất khi bạn đóng trình duyệt.Dữ liệu không được gửi lên Server. Thông tin lưu trữ nhiều hơn cookie (ít nhất 5MB).

- **Cookie** thông tin được gửi lên server: Cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng, mỗi khi người dùng tải ứng dụng, trình duyệt sẽ gửi cookie để thông báo cho ứng dụng về hoạt động trước đó của bạn. Vì vậy đừng bao giờ lưu trữ những thông tin quan trọng, yêu cầu tính bảo mật cao vào cookie vì nó hoàn toàn có thể bị sửa đổi và đánh cắp, thấp chí có thể lợi dụng điều này để tấn công website của bạn. Cookie chủ yếu là để đọc phía máy chủ (cũng có thể được đọc ở phía máy khách), localStorage và sessionStorage chỉ có thể được đọc ở phía máy khách. Có thời gian sống: Mỗi cookie thường có khoảng thời gian timeout nhất định do lập trình viên xác định trước. Lưu trữ: cho phép lưu trữ tối đa 4KB và vài chục cookie cho một domain.

- **DOM** là tên gọi viết tắt của (Document Object Model – tạm dịch Mô hình Các Đối tượng Tài liệu). Là một chuẩn được định nghĩa bởi W3C (Tổ Chức Web Toàn Cầu – World Wide Web Consortium). DOM được dùng để truy xuất và thao tác trên các tài liệu có cấu trúc dạng HTML hay XML bằng các ngôn ngữ lập trình thông dụng như Javascript, PHP…

- **BOM** là chữ viết tắt của Browser Object Model, hay còn gọi là các đối tượng liên quan đến trình duyệt - browser

```
window
screen
location
history
navigator
popup
timing
cookies
```

- **Bubbling and capturing**

  - **Bubbling** khi một sự kiện xảy ra trên một phần tử, đầu tiên nó chạy các trình xử lý trên nó, sau đó chạy trên cha của nó, sau đó tiếp tục lên các tổ tiên khác.

  - **capturing** nắm bắt.

- **Regular-expressions** is a sequence of characters that forms a search pattern.

  - Syxtax

```
/pattern/modifiers;
```

```
/w3schools/i;
// /w3schools/i  is a regular expression. w3schools is a pattern (to be used in a search). i is a modifier (modifies the search to be case-insensitive).
```
