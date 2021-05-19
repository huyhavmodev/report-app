# **_Review JS_**

Array
- Linked list
+ Linked list hay danh sách liên kết là một dang cấu trúc dữ liệu tuyến tính trong đó các phần tử được liên kết với nhau nhờ các links, mỗi phần tử bao gồm phần chứa dữ liệu và phần liên kết đến phần tử kế tiếp. Phần tử cuối cùng của danh sách liên kết sẽ trỏ đến giá trị NULL để đánh dấu điểm cuối.

+ Tương tự như mảng, linkedlist được sử dụng phổ biến để tổ chức dữ liệu hỗ trợ cho việc lưu trử và tìm kiếm dữ liệu.

+ Có 3 loại là danh sách liên kết đơn, danh sách liên kết đôi và danh sách liên kết xoay vòng.

Ưu điểm của linkedlist so với array: kích thước linh hoạt, dễ dàng thêm và xóa phần tử, không yêu cầu cấp phát trước bộ nhớ.
Ưu điểm của array so với linkedlist: truy xuất ngẫu nhiên, lượng bộ nhớ yêu cầu thấp, dễ thực thi và sử dụng.


- Queue (hàng đợi FIFO) 

- Stack (ngăn xếp - LIFO)

- Hash table

 hash table là một cấu trúc dữ liệu dùng để lưu theo các cặp key value, nó dùng hash function để tính toán tới một index, nơi lưu trữ một bucket các giá trị rồi từ đó sẽ retrieve ra value, mục tiêu là để độ phức tạp ở mức O(n)

- Set
 Giông như Array nhưng phần tử là unique. Không lặp lại
- Tree
  Đường: là một dãy các nút cùng với các cạnh của một cây.

  Nút gốc (Root): nút trên cùng của cây được gọi là nút gốc. Một cây sẽ chỉ có một nút gốc và một đường xuất phát từ nút gốc tới bất kỳ nút nào khác. Nút gốc là nút duy nhất không có bất kỳ nút cha nào.

  Nút cha: bất kỳ nút nào ngoại trừ nút gốc mà có một cạnh hướng lên một nút khác thì được gọi là nút cha.

  Nút con: nút ở dưới một nút đã cho được kết nối bởi cạnh dưới của nó được gọi là nút con của nút đó.

  Nút lá: nút mà không có bất kỳ nút con nào thì được gọi là nút lá.

  Cây con: cây con biểu diễn các con của một nút.

  Truy cập: kiểm tra giá trị của một nút khi điều khiển là đang trên một nút đó.

  Duyệt: duyệt qua các nút theo một thứ tự nào đó.

  Bậc: bậc của một nút biểu diễn số con của một nút. Nếu nút gốc có bậc là 0, thì nút con tiếp theo sẽ có bậc là 1, và nút cháu của nó sẽ có bậc là 2, …

  Khóa (Key): biểu diễn một giá trị của một nút dựa trên những gì mà một thao tác tìm kiếm thực hiện 
  trên nút.

Cây tìm kiếm nhị phân biểu diễn một hành vi đặc biệt. Con bên trái của một nút phải có giá trị nhỏ hơn giá trị của nút cha (của nút con này) và con bên phải của nút phải có giá trị lớn hơn giá trị của nút cha (của nút con này



- Graph

Một dạng biểu diễn hình ảnh của một tập các đối tượng, trong đó các cặp đối tượng được kết nối bởi các link. Các đối tượng được nối liền nhau được biểu diễn bởi các điểm được gọi là các đỉnh (vertices), và các link mà kết nối các đỉnh với nhau được gọi là các cạnh (edges). Biểu diễn thành dạng Ma trận.

AJAX and JSON
- AJAX - Asynchronous JavaScript and XML. Nó là một bộ các kỹ thuật thiết kế web giúp cho các ứng dụng web hoạt động bất đồng bộ – xử lý mọi yêu cầu tới server từ phía sau.
- JSON là viết tắt của JavaScript Object Notation

{
    "name" : "TopDev",
    "title" : "Việc làm IT cho Top Developers",
    "description" : "là hệ sinh thái bao gồm cộng đồng các Top Developers."
}

promise, async await

  Promise là cơ chế trong JavaScript giúp bạn thực thi các tác vụ bất đồng bộ mà không rơi vào callback hell hay pyramid of doom, là tình trạng các hàm callback lồng vào nhau ở quá nhiều tầng.
  Các tác vụ bât đồng bộ có thể kể đến là:
    + Ajax
    + setTimeOut
    + setInterval

    Khởi tạo promise (result, reject)
      const p = new Promise(
    /* executor */ function(resolve, reject) {
      // Thực thi các tác vụ bất đồng bộ ở đây, và gọi `resolve(result)` khi tác
      // vụ hoàn thành. Nếu xảy ra lỗi, gọi đến `reject(error)`.
    },
  )

  Trong đó, executor là một hàm có hai tham số:

  resolve là hàm sẽ được gọi khi promise hoàn thành
  reject là hàm sẽ được gọi khi có lỗi xảy ra

  Handle Promise bằng 2 cách :
  + .then ... .catch: 
  + Async/ Await (ES7):  thực hiện các thao tác bất đồng bộ một cách tuần tự hơn.  
  Async/await vẫn sử dụng Promise ở bên dưới nhưng mã nguồn của bạn (theo một cách nào đó) sẽ trong sáng và dễ theo dõi.
  Để sử dụng, bạn phải khai báo hàm với từ khóa async. Khi đó bên trong hàm bạn có thể dùng await.

  
ajax request (Fetch API, Axios)
- Bất đồng bộ trong Javascript và XML
- Tạo background HTTP request với Javascript
- Thực thi response của HTTP requests với Javascript
- Không cần load lại trang page

=> Sử dụng trong web SPA(Single page application) hoặc web không cần load lại trang
- Tương tác với DOM qua JS

ES6: scope, arrow function, template string, destructuring, default parameter, rest, spread,...
- Scope: Với việc có thêm let, const thì ta sẽ có block scope và function scope
- Arrow function: Cách viết ngắn gọn lại function
- Template string: Chuỗi mâu với` Xin chào ${varrible} `. Đặt câu lệnh nằm trong ``, ta sẽ sử dụng được biến ${varribale}
- destructuring
Destructuring là một cú pháp cho phép bạn gán các thuộc tính của một Object hoặc một Array. Điều này có thể làm giảm đáng kể các dòng mã cần thiết để thao tác dữ liệu trong các cấu trúc này. Có hai loại Destructuring: Destructuring Objects và Destructuring Arrays.

- default parameter
Tham số mặc định khi truyền vào 1 hàm. Ví dụ: (a, b = 1)
- rest
Tham sô truyền vào hàm với dạng ...theArs

 Đôi khi chúng ta phải thiết kế một số Api có thể chấp nhận n số tham số

 function sum(...numbers){
  return numbers.reduce((sum, val)=>{
      return sum += val;
    });
}
sum(3,5) // gives 8
sum(1,2, 3, 5) //gives 11.

- spread
* Lưu ý tới tính mutable và immutable trong javascript
* Khi dùng spread sẽ không cần lo. Copy nhưng không copy địa chỉ address.
  var new_arr  = ['a', 'b', 'c', 'd'];
  var new_arr2 = new_arr;
  new_arr2.push('e');

  console.log(new_arr);//  ["a", "b", "c", "d", "e"]
  console.log(new_arr2);// ["a", "b", "c", "d", "e"]

  var new_arr  = ['a', 'b', 'c', 'd'];
  var new_arr2 = [...new_arr];
  new_arr2.push('e');
  console.log(new_arr);  // Output 'a', 'b', 'c', 'd'
  console.log(new_arr2); // Output 'a', 'b', 'c', 'd', 'e'

 copy properties của một object sang một object khác 

- Destructure sử dụng để tạo ra một new variables từ array items, hoặc object properties
- Spread syntax sử dụng để unpack terables của một arrays, objects, và function calls
- Rest parameter là một cú pháp tạo ra một array từ một số lượng giá trị không xác định

Git:
- Tìm hiểu git căn bản
+ git clone 
+ git pull
+ git push

- Hiểu về các server sử dụng git: Bitbucket, Github, Gitlab ...
- Tìm hiểu vắn tắt nội dung về git

. Các trạng thái của git
   - Stage: các file được đưa vào staging area (git add <file>)
   - Unsage: các file ở trạng thái thay đổi chưa được thêm vào staging area  (git rm --cached <file>)


 git init: 
  - git add <path_file>: đưa file vào staging area
  - git rm --cached <file>: đưa file từ staging area sang trạng thái Unsage
  - git rm --cached -r <folder>:
  - git remote -v: hiển thị link remote reposistory
  - git remote remove <remote_name>: xóa remote_name
  - git remote add <remote_name> <remote_url_server_git>: thêm remote_url với định danh remote_name vào 1 project git
  => Việc xóa và add remote origin có ý nghĩa gì? Có thể add nhiêu remote origin không? Nếu không

Branch ============
  - git checkout -b <branch_name>: Tạo branch mới đồng thời switch sang branch đó
  - git checkout <branch_name>: switch sang nhánh khác (Điều kiện nhánh đó phải tồn tại)
  - git branch -D <branch_name>: Xóa 1 branch
  - git 


- Làm bài tập về git
- JS test (50% - DONE hàm, còn unit test )