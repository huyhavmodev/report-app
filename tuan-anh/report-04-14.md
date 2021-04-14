Regex
- Regex là các mẫu (pattern) thay vì các chuỗi cụ thể được sử dụng
tìm/thay thế (Find/Replace). Là một công cụ cực mạnh cho xử lí 
chuỗi trong Php, javascript…
- Sử dụng để thay thế, sửa đổi và lọc string bằng các phwuong pháp
match, replace, search...
Regex đơn giản:
    var regex = /hello/;
    var str = 'hello world';
    var result = regex.test(str);
    console.log(result);
    // returns true