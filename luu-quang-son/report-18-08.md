**Life cycle - HOOKS**
**Life cycle Component** gồm 3 nhóm, ứng với 4 giai đoạn của component: Mounting, Updating, Unmounting, Error Handling.
            -- Mounting
            Nó sẽ theo thứ tự sau
            constructor()
            static getDerivedStateFromProps()
            render()
            componentDidMount()

            -- Updating
            Các phương thức này sẽ được gọi khi có sự thay đổi của state hoặc props
            static getDerivedStateFromProps()
            shouldComponentUpdate()
            render()
            getSnapshotBeforeUpdate()
            componentDidUpdate()
            
            -- Unmounting

            Phương thức được gọi trước khi remove component khỏi DOM

            componentWillUnmount()
            Error Handling

            Bất kể lỗi ở đâu trong component, nó sẽ gọi đến phương thức này

            componentDidCatch() 

    --  render() là phương thức bắt buộc duy nhất khi tạo ra một component, bắt buộc trả về một trong những giá trị
        React element
        Arrays and fragments
        Portals
        String and numbers
        Booleans or null 
        Hàm này sẽ không được gọi nếu shouldComponentUpdate() return false
    
    -- componentDidMount() gọi lại sau mỗi lần re-render. Hàm này thường sử dụng cho call api.
```js
        componentDidMount() {
  fetch('https://gitconnected.com')
    .then((res) => {
      this.setState({
        user: res.user
      });
    });
}
```
    -- componentDidUpdate() hàm này sẽ được gọi sau khi component cập nhật. Hàm này sẽ k được gọi sau lần render đầu tiên.

    -- componentWillUnmount() sử dụng để remove các listener, các hàm setInterval, cancel network request
```js
            componentWillUnmount() {
  window.removeEventListener('resize', this.resizeEventHandler);
}
```
    -- shouldComponentUpdate() hàm này cải thiện perfomence của react.


**HOOKS** : chỉ sử dụng với function component.
**USESTATE** cho phép chúng ta khai báo local state trong Function Component 
```js
        const [state, setState] = useState(initialStateValue)
            //state: định nghĩa tên của state nó có thể là đơn giá trị hoặc object,.. (là thamg số của useState)
            // setState: định nghĩa tên function dùng cho việc update state (là thamg số của useState)
            // initialStateValue: là giá trị ban đầu của state
```
```js
      const Example =  () => {
        const [count, setCount] = useState(0)
        const handleClick = () => setCount(age + 1)

        return (
            <div>
            Current count {count}.
            <div>
                <button onClick={handleClick}>Increment Count!</button>
            </div>
            </div>
        )
        }
        export default Example;
```


**USEEFFECT** giống với componentDidMount() trong class Component. UseEffect( là 1 sideEffect :những hành động event có thể làm thay đổi DOM trong react components ) giúp xử lý logic trong Function Component.
    -- useEffect nhận vào 1 hàm và được gọi sau mỗi lần component render. Ta truyền thêm 1 empty array dependence để tránh hàm này chạy lại sau mỗi lần render.

```js
        useEffect(()=> {
                console.log('useEffect')
        },[]);
```

**useMemo**   caching lại giá trị return của function, mỗi lần component rerender nó sẽ kiểm tra giá trị tham số truyền vào function nếu giá trị đó không thay đổi, thì return value đã caching trong memory. Ngược lại nếu giá trị tham số truyền vào thay đổi, nó sẽ thực hiện tính toán lại vào trả về value, sao đó caching lại value cho những lần rerender tiếp theo
        -- useMemo có 2 tham số đó là function và một list dependencies, nó sẽ memorizes value output của một function và chỉ recomputed memoried value này khi mà một trong các dependencies thay đổi
        -- useMemo giúp tăng hiệu suất của App.
```js
        const numbers = useMemo(() => {
            console.log('useMemo')
        },[])
    ;
```

**useReducer** nhận vào reducer và initialState khởi tạo ban đầu, trả về state hiện tại và dispatch function dùng để trigger 1 action
```js
        const [state, dispatch] = useReducer(reducer , 0);
```

        --  Example (https://viblo.asia/p/su-dung-usereducer-hook-trong-react-L4x5x19wKBM)
```js
        
```