# NGUYỄN THÀNH LUÂN - Report 08/13:

**ReactJS**

**Install ReactJS and Tailwind CSS**
- Done!

**JSX**
- Là viết tắt là Javascript XML, nó cho phép bạn viết các đoạn mã HTML trong React một cách dẽ dàng và có cấu trúc hơn
- Cú pháp: thay class = className
```js
    <p className="text">ReactJS</p>
```

**Components and Props**
- Components: là các thành phần giao diện cụ thể, 1 website sẽ gồm nhiều components đươc ghép lại và sắp xếp hợp lý.
    + function components và class components
```js
    // function components
    function App() {
        return (
            <div className="App">
                <h1>Hello ReactJS</h1>
            </div>    
     );
    }
    export default App;

    // clas components
    class App extends React.Component {
        render() {
            return(
            <>
                <h1>Hello ReactJS</h1>
            </>
            );
        }
    }
    export default App;
```
- Props: là một object được truyền vào trong một components, mỗi components sẽ nhận vào props và trả về react element.
    + Props cho phép chúng ta giao tiếp giữa các components với nhau bằng cách truyền tham số qua lại giữa các components.
    + Khi một components cha truyền cho component con một props thì components con chỉ có thể đọc và không có quyền chỉnh sửa nó bên phía components cha.

```js
    // function components
    function Welcome(props) {
        return(
            <div className="Welcome">
                <h2>Hello: {props.name}</h2>
            </div>
        );
    }

    // class components: thêm từ khóa 'this'
    class Welcome extends React.Component {
        render() {
            return(
                <>
                    <h2>Hello: {this.props.name}<h2>
                </>
            );
        }
    }
```