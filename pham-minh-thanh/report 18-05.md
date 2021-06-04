# **_Review Html/css/js/Nodejs_**

- web development - JS stack

Week 1:

Hoisting
- Hoisting là khái niệm chỉ việc mọi khai báo biến (với từ khóa var) sẽ được chuyển lên trên cùng của hàm
- Khi một file javascript compiled bởi browser, nhưng trước khi nó thực sự executed thì Function declaration 
  sẽ được stored in memory và được đẩy lên nhưng chính xác ta vẫn nhìn nó vẫn ở vị trí cũ. Và khi javascript file 
  thực sự run thì browser thực sự đã biết những function đó trước khi đọc code của file javascript. 
- Từ ES6 trở lên khi dùng const, let thì không còn bị hoisting

Scope và Closure
- Scope hay phạm vi của biến, phân loại gồm các kiểu như:
+ Global Scope (toàn cục)
+ Local Scope (chỉ có tác dụng trong hàm)
+ Function Scope (cục bộ trong hàm)
+ Block Scope (Được khai báo trong các block {} với if, while,switch, for...)
+ Lexical Scope(function sử dụng một biến của một hàm nó lòng trong, hoặc nhiều hàm lòng vào nhau.)


- Closure
+ Closure là một hàm được viết lồng vào bên trong một hàm khác (hàm cha)

for (var i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000)
}

// logs 3, 3, 3

Chúng ta thấy rằng function anonymous để console biến i của cha nó sẽ chạy sau khi cha nó chạy xong 
(Vì thằng này delay ít nhất 1s), vì vậy javascript sẽ tạo ra closure để cung cấp cho thằng hàm con trong có thể sài, 
vì vòng lặp là 3 nên sẽ tạo ra 3 closure

Giờ xem xét cái lexical enviroment nào, t biết rằng var i tuân thủ nguyên tắc function scope nó sẽ được 
tạo mới trong mỗi function còn ngoài function thì var i nhiều lần cũng chỉ là biến i đó thôi. 
Vậy chúng nó sài chung lexical enviroment.

Mà để hàm thực thi function log i ra cần tới 1s sau, vậy theo như ví dụ trên, 
vòng lặp for sẽ được chạy xong trước khi thực thi function log i sớm nhất được thực thi vậy 
biến i lúc này sẽ luôn là giá trị sau khi chạy xong vòng for, i = 3.

Vậy sẽ ra kết quả là 3, 3, 3

Để sửa lỗi này t có nhiều cách nhưng mình sẽ đề xuất một cách là dùng let thay cho var 
vì let theo nguyên tắc block scope biến sẽ được tạo mới trong dấu { } nên sẽ có 3 closure dùng 
3 lexical enviroment khác nhau nhé

for (let i = 0; i < 3; i++) {
    setTimeout(function() {
        console.log(i);
    }, 1000)
}

// logs 0, 1, 2

Object, Prototype & Inheritance
+ Object
+ Prototype

var bangai = {
	name: 'dao thi mo',
	pay: function() {
		thangdaigai.pay();
	}
};
var thangdaigai = {
	name: 'thang dai gai',
	pay: function() {
		console.log('Da mua boi tien cua bo me');
	}
};
bangai.pay(); //Da mua boi tien cua bo me

Ví dụ, có prototype và không có: 
Không có: 
  function Cat(name, color){

  　　this.name = name;

  　　this.color = color;

  　　this.type = "dongvat";

  　　this.eat = function(){
          console.log(' an ca')
      }
  }
  Sau đó tôi dùng new để tạo hai Object.

  var cat1 = new Cat('Sen', 'pink')
  console.log(cat1.eat()) //  an ca
  console.log(cat1.type) // dongvat

  var cat2 = new Cat('Boss', 'black');
  console.log(cat2.eat()) //  an ca
  console.log(cat2.type) // dongvat

console.log(cat1.eat === cat2.eat); //false

Mặc dù nhìn giống nhau nhưng nó khác địa chỉ ô nhớ (Giống như so sánh array và object)

 　function Cat(name, color){

　　　　this.name = name;

　　　　this.color = color;
　　}
    Cat.prototype.type = 'dongvat';
    Cat.prototype.eat = function() {
      console.log('an ca')
    }

  Sau đó tôi dùng new để tạo hai Object.

  var cat1 = new Cat('Sen', 'pink')
  console.log(cat1.eat()) //  an ca
  console.log(cat1.type) // dongvat

  var cat2 = new Cat('Boss', 'black');
  console.log(cat2.eat()) //  an ca
  console.log(cat2.type) // dongvat

console.log(cat1.eat === cat2.eat); //true

-> Đã cùng trỏ vào 1 ô nhớ 

+Inheritance: kế thừa trong OOP, bắt đầu có từ ES6

Condition statement (if...else, conditional (ternary) operator)

+ Câu lệnh điều kiện if else 
+ conditional (ternary) operator ( toán tử 3 ngôi ):

varible = ex1 ? ex2 : ex3

Check ex1 -> Nếu true thì return ex2 còn không thì return ex3

Data type: String, Number, Boolean, Null, Undefined, Symbol, Date, Object, Array
+ String (chuỗi)
+ Number (số)
+ Boolean ( true/false)
+ Null (Giá trị Rỗng)
+ Undefined (Khai báo nhưng chưa gán giá trị)
+ Symbol (kí tự)
+ Date (ngày tháng năm)
+ Object 
+ Array (Mảng)

Immutable/Mutable, Pass by Value/Reference
+ Immutable/Mutable:
   Immutable: Không thay đổi 
    Tất cả các kiểu primitive trong js đều là immutable.
    Khi so sánh 2 biến có kiểu primitive với nhau thì chúng sẽ so sánh giá trị:
  
  1.
  var a = 3

  function test(b) {
    // b và a ở đây đều có cùng một địa chỉ bộ nhớ.
    b = 4
  }

  test(a)

  console.log(a)   // 3
  
  2.
  function test(b) {
    b = {item: "changed"}
  }

  var a = {item: "unchanged"}
  test(a)
  console.log(a)      // {item: "unchanged"}

khi giá trị của biến không bị ghi đè mà được copy sang một nơi khác thì đó mới là immutable , 
từ giá trị ở định nghĩa này chính là giá trị đi với ô nhớ.

  - Mutable: Có thể thay đổi được . Object, array đều là mutable

  function test(b) {
    b.item = "changed"
  }

  var a = {item: "unchanged"}
  test(a)
  console.log(a)      // {item: "changed"}

+ Pass by Value/Reference:

  • CPU xử lý dữ liệu thông qua địa chỉ bộ nhớ nên thứ được truyền vào hàm luôn luôn 
  là địa chỉ bộ nhớ chứ không phải là giá trị.
  • Pass-by-value và pass-by-reference không có định nghĩa cụ thể nào và có thể 
  hiểu khác nhau với từng ngôn ngữ. Nhưng đều có chung một nguyên lý là:
  • Pass-by-value được hiểu là khi bạn thay đổi biến trong hàm thì ngoài hàm sẽ 
  không bị ảnh hưởng. Nó giống như bạn copy giá trị của biến vào biến khác rồi truyền vào hàm.
  • Pass-by-reference là khi bạn thay đổi biến trong hàm cũng làm ngoài hàm bị ảnh hưởng.
    Nó giống như bạn truyền đúng địa chỉ của biến đó vào hàm.
  • Khi chương trình thực thi, dữ liệu trên RAM có thể được lưu trữ trên stack hoặc heap 
  nhưng việc tham chiếu bằng địa chỉ giữa các biến là như nhau nên để cho đơn giản mình sẽ 
  giả sử chúng chỉ được lưu trữ trên stack.
  • Trong tất cả ngôn ngữ, khi khai báo một hàm thì tham số của hàm có thể khác 
  hoặc trùng với tên biến được truyền vào hàm.


this, apply, call, bind
- call Gọi hàm và cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy (Comma)
  function.call(thisArg, arg1, arg2, ...) 

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting1, greeting2) {
 console.log(greeting1 + ',' + greeting2 + ' ' + this.firstName + ' ' + this.lastName);
}

say.call(person1, 'Hello', 'Good morning'); // => Hello,Good morning Jon Kuperman
say.call(person2, 'Hello', 'Good morning'); // => Hello,Good morning Kelly King

- apply Gọi hàm và cho phép bạn truyền vào một object và các đối số thông qua mảng (Array)
  fun.apply(thisArg, [argsArray])

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting0, greeting1) {
console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
}

say.apply(person1, ['Hello', 'Good moring']); // => Hello,Good moring Jon Kuperman
say.apply(person2, ['Hello', 'Good moring']); // => Hello,Good moring Kelly King

- bind - Trả về một hàm số mới, cho phép bạn truyền vào một object và các đối số phân cách nhau bởi dấu phẩy.

var person1 = {firstName: 'Jon', lastName: 'Kuperman'};
var person2 = {firstName: 'Kelly', lastName: 'King'};

function say(greeting0, greeting1) {
 console.log(greeting0 + ',' + greeting1 + ' ' + this.firstName + ' ' + this.lastName);
}

var sayHelloJon = say.bind(person1, 'Hello', 'Good morning');
var sayHelloKelly = say.bind(person2, 'Hello', 'Good morning');

sayHelloJon(); // => Hello,Good morning Jon Kuperman
sayHelloKelly(); // => Hello,Good morning Kelly King


Nhìn chung, hàm call và apply là gần giống nhau. Chúng đều gọi hàm trực tiếp. 
Chỉ khác ở cách truyền tham số vào (với call thì đối số phân cách bởi dấu phẩy comma và với apply thì đối số cho bởi mảng array)
Hàm bind thì hơi khác hơn một chút. Hàm này không gọi hàm trực tiếp mà nó sẽ trả về một hàm mới. 
Và bạn có thể sử dụng hàm số mới này sau. Về cách truyền tham số vào thì nó giống với hàm call.


- this - con trỏ this. Dựa vào ngữ cảnh ta có thể dùng this để thay thế.

setTimeout/clearTimeout
- setTimeout: Hàm setTimeout() dùng để thiết lập một khoảng thời gian 
nào đó sẽ thực hiện một nhiệm vụ nào đó và nó chỉ thực hiện đúng một lần.
- hủy bỏ thực thi nhiệm vụ đã được thiết lập trong setTimeout.

setInterval/clearInterval
- Hàm setInterval() có cú pháp và chức năng giống như hàm setTimeout(), 
tuy nhiên với hàm setInterval() thì số lần thực hiện lã mãi mãi.
- xóa đi nhiệm vụ mà ta đã thiết lập trong hàm setInterval

requestAnimationFrame/cancelAnimationFrame 

requestAnimationFrame: gửi request đến trình duyệt thực hiện một hành động update/draw frame mới thông qua tham số callback. 
Các request này sẽ được lưu trong đối tượng document với các cặp <handle, callback> và được thực hiện lần lượt. 
Giá trị handle là một số định danh được tạo ra và trả về sau khi gọi phương thức này.

cancelAnimationFrame: hủy một request được tạo ra requestAnimationFrame với tham số là handle của request.

cookie/localStorage/sessionStorage
+ Local storage:
Khả năng lưu trữ vô thời hạn: Có nghĩa là chỉ bị xóa bằng JavaScript, hoặc xóa bộ nhớ trình duyệt, hoặc xóa bằng localStorage API.
Lưu trữ được 5MB: Local Storage cho phép bạn lưu trữ thông tin tương đối lớn lên đến 5MB, lưu được lượng thông tin lớn nhất trong 3 loại.
Không gửi thông tin lên server như Cookie nên bảo mật tốt hơn.

+ Session Storage
Lưu trên Client: Cũng giống như localStorage thì sessionStorage cũng dùng để lưu trữ dữ liệu trên trình duyệt của khách truy cập (client).
Mất dữ liệu khi đóng tab: Dữ liệu của sessionStorage sẽ mất khi bạn đóng trình duyệt.
Dữ liệu không được gửi lên Server
Thông tin lưu trữ nhiều hơn cookie (ít nhất 5MB)

+ Cookie: Thông tin được gửi lên server: Cookie sẽ được truyền từ server tới browser và được lưu trữ trên máy tính của bạn khi bạn truy cập vào ứng dụng, 
mỗi khi người dùng tải ứng dụng, trình duyệt sẽ gửi cookie để thông báo cho ứng dụng về hoạt động trước đó của bạn. 
Vì vậy đừng bao giờ lưu trữ những thông tin quan trọng, yêu cầu tính bảo mật cao vào cookie vì nó hoàn toàn có thể bị sửa đổi và đánh cắp, thậm chí có thể lợi dụng điều này để tấn công website của bạn.
+ Cookie chủ yếu là để đọc phía máy chủ (cũng có thể được đọc ở phía máy khách), localStorage và sessionStorage chỉ có thể được đọc ở phía máy khách.
+ Có thời gian sống: Mỗi cookie thường có khoảng thời gian timeout nhất định do lập trình viên xác định trước.

Windonw:
- DOM
- BOM 
- Javascript


DOM - Document Object Model - Mô hình Các Đối tượng Tài liệu




BOM - Browser Object Model - các đối tượng liên quan đến trình duyệt - browser.

window
screen
location
history
navigator
popup
timing
cookies
frames
XMLHttpRequest


Callback
Callback là một hàm sẽ được thực hiện sau khi một hàm khác đã thực hiện xong 

Array
- typeof: object
- Reference type

Multidimensional  (mảng nhiều chiều)

var as2D = [ 
 ["a","b","c","d","e","f","g","h","i","j"], 
 ["A","B","C","D","E","F","G","H","I","J"], 
 ["!","@","#","$","%","^","&","*","(",")"] 
 ];

Access and Iterate Through an Array
- for ... in
- for ... of
- find, map, filter
- sort
...

Bubbling and capturing
+ Bubbling: Khi một sự kiện xảy ra trên một phần tử, trước tiên nó chạy các trình xử lý trên nó, sau đó là cha mẹ của nó, sau đó tiếp tục lên các tổ tiên khác.

+ capturing: Bắt giữ


Regular-expressions

var patt = /w3schools/i

/w3schools/i  is a regular expression.
w3schools  is a pattern (to be used in a search).
i  is a modifier (modifies the search to be case-insensitive).

Modifiers:
g	- Perform a global match (find all matches rather than stopping after the first match)
i	- Perform case-insensitive matching
m	- Perform multiline matching

Brackets:
[abc]	- Find any character between the brackets
[^abc] - Find any character NOT between the brackets
[0-9]	- Find any character between the brackets (any digit)
[^0-9]	- Find any character NOT between the brackets (any non-digit)
(x|y)	- Find any of the alternatives specified

Metacharacters:

.	Find a single character, except newline or line terminator
- \w	Find a word character
- \W	Find a non-word character
- \d	Find a digit
- \D	Find a non-digit character
- \s	Find a whitespace character
- \S	Find a non-whitespace character
- \b	Find a match at the beginning/end of a word, beginning like this: \bHI, end like this: HI\b
- \B	Find a match, but not at the beginning/end of a word
- \0	Find a NULL character
- \n	Find a new line character
- \f	Find a form feed character
- \r	Find a carriage return character
- \t	Find a tab character
- \v	Find a vertical tab character
- \xxx	Find the character specified by an octal number xxx
- \xdd	Find the character specified by a hexadecimal number dd
- \udddd	Find the Unicode character specified by a hexadecimal number dddd


- Quantifiers:
- n+	Matches any string that contains at least one n
- n*	Matches any string that contains zero or more occurrences of n
- n?	Matches any string that contains zero or one occurrences of n
- n{X}	Matches any string that contains a sequence of X n's
- n{X,Y}	Matches any string that contains a sequence of X to Y n's
- n{X,}	Matches any string that contains a sequence of at least X n's
- n$	Matches any string with n at the end of it
- ^n	Matches any string with n at the beginning of it
- ?=n	Matches any string that is followed by a specific string n
- ?!n	Matches any string that is not followed by a specific string n

-Week 2:

- Array (mảng)
- Linked list (danh sách liên kết)
- Queue 
- Stack 
- Hash table
- Set
- Tree
- Graph

- HTML/CSS test (DONE)
- https://3f03t.csb.app/