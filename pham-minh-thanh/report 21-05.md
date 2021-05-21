# **_Typescript_**

Lợi thế:

- Với static typing, code viết bằng TypeScript dễ dự đoán hơn, và dễ debug hơn.
- Dễ dàng tổ chức code cho các ứng dụng cực lớn và phức tạp nhờ modules, namespaces và hỗ trợ OOP mạnh mẽ.
- TypeScript có một bước biên dịch thành JavaScript, sẽ bắt tất cả các loại lỗi trước khi chúng chạy và làm hỏng một vài thứ.
- Framework Angular 2 viết với TypeScript và nó cũng khuyến khích các lập trình viên sử dụng ngôn ngữ này trong các dự án của họ.

- Static Typing: 
  - Khai báo biến:
    var burger: string = 'hamburger',
  - Truyền tham số
  function speak(food: string, energy: number): void {
    console.log("Our " + food + " has " + energy + " calories.");
  }

Một số kiểu dữ liệu trong Typescript:

- Number – Tất cả giá trị số được biểu diễn bởi kiểu number, không có định nghĩa riêng cho số nguyên (interger), số thực (float) hoặc các kiểu khác.
  let decimal: number = 6;
  let hex: number = 0xf00d;
  let binary: number = 0b1010;
  let octal: number = 0o744;
  let big: bigint = 100n;
- String – Giống như string của JavaScript có thể được bao quanh bởi ‘dấu nháy đơn’ hoặc “dấu nháy kép”.
  let color: string = "blue";
  color = 'red';

- Boolean – true hoặc false, sử dụng 0 và 1 sẽ gây ra lỗi biên dịch.
  let isDone: boolean = false;  
- Any – Một biến với kiểu này có thể có giá trị là một string, number hoặc bất kỳ kiểu nào.
- Arrays – Có 2 kiểu cú pháp: my_arr: number[]; hoặc my_arr: Array<number>.
  let list: number[] = [1, 2, 3];
  let list: Array<number> = [1, 2, 3];

- Tuple - Mảng định sẵn số lượng phần tử con và kiểu dữ liệu của chúng.
/ Declare a tuple type
  let x: [string, number];

- Void – Được sử dụng khi hàm không trả lại bất kỳ giá trị nào. (same C/C++)

- Enums: kiểu dữ liệu đặc biệt cho phép một biến có thể là một tập hợp các hằng số định sẵn.
  enum Role {
    FRESHER = 'NEWBIE',
    JUNIOR = 100,
    SENIOR
  };

- Null và Undefined: có thể gán cho các kiểu dữ liệu khác
  let u: undefined = undefined;
  let n: null = null;

Interfaces

- Interfaces được sử dụng để kiểm tra, xem một đối tượng có phù hợp với một cấu trúc nhất định hay không. Bằng cách định nghĩa một interface, chúng ta có thể đặt tên một sự kết hợp đặc biệt của các biến, đảm bảo rằng chúng luôn luôn đi cùng nhau.

Khi chuyển thành JavaScript, interface biến mất – mục đích duy nhất của chúng là trợ giúp trong giai đoạn giai đoạn phát triển.


  // Here we define our Food interface, its properties, and their types.
  interface Food {
      name: string;
      calories: number;
  }

  // We tell our function to expect an object that fulfills the Food interface. 
  // This way we know that the properties we need will always be available.
  function speak(food: Food): void{
    console.log("Our " + food.name + " has " + food.calories + " calories.");
  }

  // We define an object that has all of the properties the Food interface expects.
  // Notice that types will be inferred automatically.
  var ice_cream = {
    name: "ice cream", 
    calories: 200
  }

  speak(ice_cream);

Classes: 

  class Menu {
    // Our properties:
    // By default they are public, but can also be private or protected.
    items: Array<string>;  // The items in the menu, an array of strings.
    pages: number;         // How many pages will the menu be, a number.

    // A straightforward constructor. 
    constructor(item_list: Array<string>, total_pages: number) {
      // The this keyword is mandatory.
      this.items = item_list;    
      this.pages = total_pages;
    }

    // Methods
    list(): void {
      console.log("Our menu for today:");
      for(var i=0; i<this.items.length; i++) {
        console.log(this.items[i]);
      }
    }

  } 

  // Create a new instance of the Menu class.
  var sundayMenu = new Menu(["pancakes","waffles","orange juice"], 1);

  // Call the list method.
  sundayMenu.list();

Generics:


# **_Web development test_**

- Hiểu các thành phần cấu tạo nên web application
+ Gồm :
+ Giao diện Front End(Client- Chứa giao diện bề ngoài của trang web, giúp người dùng có thể tương tác qua các nút bấm hay thanh cuộn, ô ...)
+ Server (Nơi xử lý các logic, nhận request từ client, xử lý yêu cầu vào gửi trả lại cho client hiển thị ra ngoài màn hình )
+ Database: Nơi lưu trữ bản ghi dữ liêu, nơi chứa dữ liệu của toàn bộ hệ thống.
- Hiểu các bước 1 request vận hành như thế nào

+ Client - Server giao tiếp thông qua giao thức HTTTP (Phương thức truyền tải siêu văn bản)

Bước 1: Request từ client đến server
Bước 2: Response từ server trả về client

- Vẽ sơ đồ hoạt động của 1 web application bắt đầu từ khi người dùng gõ 1 địa chỉ web site lên thanh address bar của trình duyệt

![alt text](https://github.com/thanhpm95/git_example/blob/main/Untitled-Diagram-1.png)



# **_Web Development - A Practical Guide_**

- Basic Tools
- HTML & CSS
- Sass
+ variables, mixins, functions, nesting ...
- CSS Frameworks
+ Boostrap, Tailwind CSS
- UI Design Practices
- Vanilla JavaScript
- Some Other Tools
- Basic Frontend Deployment
- Domain Names, SSL, etc
- Foundational Frontend Developer Summary
- Frontend Frameworks
- State Management
- TypeScript
- Testing
  + Unit Tests (dev):
  + Integration Tests (tester):
  + End to End Tests (tester):
- Server Side Rendering
+ Next.js: react
+ Nuxt.js: Vue
+ Angular Universal: Angular
+ Sapper (Svelte)
- Static Site Generators
- Static site generator đã và đang giúp cho cộng đồng frontend developer có công cụ mạnh mẽ để xây dựng website mà không cần phải có kiến thức về backend.
- Headless CMS

- The Jamstack: JAMstack là khái niệm mô tả cách xây dựng website dựa trên 3 thành phần Javascript, APIs, Markup.
- Javascript: Đóng vai trò chính trong việc xây dựng hệ thống. Là phần frontend có nhiệm vụ kết nối APIs và hiển thị content (Markdown) cho người dùng
- APIs: là các third-party, SaaS được tích hợp vào hệ thống
- Markup: cách thức để trình bày nội dung, phổ biến nhất là Markdown. Markdown sử dụng các cú pháp đơn giản, dễ hiểu, dễ đọc, dễ tiếp cận hơn HTML. Markdown được ưu ái vì nó dễ dàng chuyển đổi sang HTML, headless CMS sử dụng markdown trong content editor. Điều này tách biệt cấu trúc nội dung trình bày (Headless cms đảm nhận) và thể hiện style của nội dung (Frontend sẽ đảm nhận phần này).

- JAMstack nổi nên như một cách thức mới để xây dựng các trang cms. Lợi ích lớn nhất mà nó mang lại bởi việc loại bỏ tầng backend, cũng như dữ liệu các trang web được sinh ra trong quá trình build —> giúp cho trang web có tốc độ load cực nhanh và chi phí cho hosting rẻ (thậm chí là free đối với nhiều nền tảng hiện có). Chính vì những ưu điểm đó mà JAMstack là cách thức được cộng đồng phát triển website quan tâm nhiều trong thời gian gần đây.

- Server Side Languages
- Server Side Frameworks
- Databases
- GraphQL
- Socket.io  & Real-Time Apps
- Deployment, Servers & DevOps
- Mobile Development
- Progressive Web Apps
- Desktop Apps With Web Tech
- AI / Machine Learning
- Web Assembly
- Algorithms
- Data Structures
- Software Design Patterns