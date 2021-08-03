## DAY2

**Condition statement** là câu điều kiện if-esle , switch - case ...
```js
var a = 10;
var b = 11;

if (a > b) {
  alert = "hello";
} else if (a = b) {
  alert = "Good day";
} else (a>b) {
  alert = "Good evening";
}
console.log(alert);
 /// Good day
```
```js 
   let day;
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
    day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case  6:
    day = "Saturday";
}
document.getElementById("demo").innerHTML = "Today is " + day;  // Today is Tuesday
```


**Data type** gồm 8 kiểu : String , Number , Undefinded , Null , Symbol , Boolean , Object.
--  |  Data Types    |     Example      |
    |----------------|--------------    |
    |String	         |'Hello world!'    |
    |Number          |3; 3.14;...       |
    |BigInt          |1n,...            |
    |Boolean         | true & false     |
    |undefined       | var x            |
    |null 			 | let x = null;    |
    |symbol			 |  var symbol = symbol();|
    |object 		 | let game = {};   |

**Immutable/Mutable, Pass by Value/Reference**
    -- Mutable là giá trị có thể thay đổi được còn Immutable là giá trị không thể thay đổi được
    -- Khi cần thay đổi một biến trong vòng lặp thì bạn nên dùng Mutable và ngược lại.
```js


