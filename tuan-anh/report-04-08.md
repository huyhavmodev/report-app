Promise:
- Promise là cơ chế xử lí Asynchronous trong JavaScript giúp chúng ta code
ngắn gọn và dễ đọc hơn, tránh rơi vào callback hell
- Promise sẽ chạy function async ở trong nó, function này sẽ nhận hai argument
là resolve và reject. resolve() là hàm sẽ chạy khi promise được hoàn thành, nếu
không thì hàm reject() sẽ chạy
- Có thể truy xuất promise object thông qua .then() nếu thành công hoặc .catch() nếu promise không thành công