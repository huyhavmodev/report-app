TypeScript Interfaces
Interfaces dùng để kiểm tra xem một đối tượng có phù hợp
với một cấu trúc nhất định hay không. Sử dụng để validate
argument của 1 function hay props của 1 React component...
VD về 1 Interface kiểm tra tham số của user:

interface User {
    name: string;
    age: number;
    address: {
        city: string;
        country: string;
    }
}

Nếu function sử dụng interface User để validate argument,
TypeScript sẽ báo lỗi ngay lập tức nếu có bất cứ input nào
không chính xác 