## Nguyen Minh Hieu - 03/31

### Topic: JSON Là gì?

#### 1. JSON là gì? 
- là một kiểu định dạng dữ liệu tuân theo một quy luật nhất định mà hầu hết các ngôn ngữ lập trình hiện nay đều có thể đọc được. JSON là một tiêu chuẩn mở để trao đổi dữ liệu trên web.
- JSON sử dụng các cặp key – value để lưu trữ và dụng, Nó hỗ trợ các cấu trúc dữ liệu như đối tượng và mảng.

``` JSON
{
    "name" : "TopDev",
    "title" : "Việc làm IT cho Top Developers",
    "description" : "là hệ sinh thái bao gồm cộng đồng các Top Developers."
}
```
- Ta có thể thấy cú pháp của JSON có 2 phần đó là key và value:

- Chuỗi JSON được bao lại bởi dấu ngoặc nhọn {}
Các key, valuecủa JSON bắt buộc phải đặt trong dấu nháy kép {“}, nếu bạn đặt nó trong dấu nháy đơn thì đây không phải là một chuỗi JSON đúng chuẩn. Nếu trường hợp trong value của bạn có chứa dấu nháy kép " thì hãy dùng dấu (\) để đặt trước nó, ví dụ  \"json là gì\".

- Nếu có nhiều dữ liệu thì dùng dấu phẩy , để ngăn cách.

- Các key của JSON bạn nên đặt chữ cái không dấu hoặc số, dấu _ và không có khoảng trắng., ký tự đầu tiên không nên đặt là số.

- File json có thể được lưu với bất kỳ phần mở rộng nào, tuy nhiên thông thường thì nó được lưu dưới phần mở rộng là .json hoặc .js.

#### 2. Nên sử dụng JSON khi nào

- Đó là khi bạn muốn lưu trữ dữ liệu đơn thuần dưới dạng metadata ở phía server. Chuỗi JSON sẽ được lưu vào database và sau đó khi cần dữ liệu thì sẽ được giải mã