# NGUYỄN THÀNH LUÂN - Report 08/12:

**Event loop**
```js
    console.log(1);
    console.log(2);
    setTimeout( function log3() {
        console.log(3);
    },0)
    console.log(4);
```
- Trong JS, khi chưa chạy lệnh thì Callstack sẽ trống. Các lệnh khi chạy sẽ được đưa lần lượt vào Callstack.
- Khi chạy đến setTimeout, function log3() sẽ được chuyển vào WebAPis. setTimeout = 0 nên chuyển function log3() xuống callback queue.
- Khi này vẫn còn console.log(4) nên function log3() vẫn chưa chạy ngay.
- Nhiệm vụ của Event loop ở đây là kiểm tra khi nào Callstack trống sẽ chuyển lệnh từ Callback queue lên Callstack để thực hiện.

- Tham khảo: http://latentflip.com/loupe

**Hoàn thiện bài test**
- Html/Css: https://codesandbox.io/s/serene-kepler-9hw46
- Js: https://codesandbox.io/s/javascript-forked-joo1z
- ReactJS 1: https://codesandbox.io/s/little-fire-xx4f9
- ReactJS 2: https://codesandbox.io/s/stupefied-kapitsa-k7882

**Tìm hiểu TypeScript**

**React JS**

**JSX**
- JSX (Javascript + XML): là 1 cú pháp mở rộng của Javascript. JSX được sử dụng để biểu thị UI components.
```js
    class HelloReact extends React.Component {
        render() {
            return (
                <>
                    <h1>Hello ReactJS</h1>
                </>
            )
        }
    }
    export default HelloReact;
```

***Component and Props**