**Vuong Tuan Anh 29/3/2021**

**Yesterday:**
-AJAX and JSON
-promise, async await
-ajax request (Fetch API, Axios)
-ES6: scope, arrow function, template string, destructuring, default parameter, rest, spread,...
-Ôn lại Algorithm, làm leetcode
-Hoàn thiệp app React giai đoạn 2

**Today:**
-Data Structures, Algorithms, leetcode
-Hoàn thiệp app React giai đoạn 2

No impediment yet.

<!-- ------------------------------------------ -->
**Day End Report**
Destructuring assignment:
-Cú pháp assignment kiểu mới của ES6, giúp chúng ta gán biến nhanh và gọn hơn

    const [a, b, c] = [1, 'string', true]
    // tương đương: const a = 1; const b = 'string'; const c = true
    
    const person = {firstname: 'John', age: 24}
    const {firstname, age} = person
    // tương đương: const firstname = 'John'; const age = 24
    
    const user = {id: 1, firstname: 'Mike'}
    function greet({ id, firstname }) {
        console.log(`I am ${firstname}`)
    // Có thể access giá trị id và firstname trong function này
    }