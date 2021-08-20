## TRAN DAI MINH 08-19

## Topic Life cycle, Hook.

- Hook bắt đầu đc ra mắt từ sau phiên bản 16.8, là những function cho phép kết nối state và lifecycle vào components. Lợi ích của việc dùng hook: giảm đáng kể số lượng code, dễ tiếp cận, cho phép sử dụng các state ngay trong function.

- state là nơi lưu trữ các value giữa các lần gọi hàm.
- useState nó trả về 1 cặp giá trị dưới dạng mảng, state hiện tại và 1 hàm để update state.
- useEffect được dùng đẻ quản lý lifecycle của 1 component, có quyền truy cập các state và props, có 2 giá trị: function để thực hiện các effect, dependency là 1 arr chưa các value khi mà value này thay đổi thì useEffect sẽ thực hiện lại.

```js
const [name, setName] = useState('');
useEffect(() => {
  setName('Minh');
});
// trường hợp này useEffect chỉ chạy 1 lần duy nhất để update lại name.
const [count, setCount] = useState(0);
useEffect(() => {
  setInterval(() => {
    setCount(count + 1);
  }, [1000]);
}, [count]);
// trường hợp này useEffect sẽ thưc hiện lại mỗi khi count tăng lên 1.
```

- Life cycle gồm 3 phần chính: Mounting, Updation, Unmounting.

- Mounting gồm có 3 phương thức: reder(),componentWillMount(),componentDidMount().

  - componentWillMount() một khi mà component được render trong lần đầu tiên thì phương thức componentWillMount sẽ được gọi trước khi render.

  - render() sẽ đực gợi sau khi componentWillMount() thực hiện xong.

  - componentDidMount() sẽ được gọi sau khi render component, ở đây cũng là nơi thực hiện các hàm AJAX, axios request, DOM hay update state sẽ được thực thi tại đây.

- Updation gôm các phương thức static getDerivedStateFromProps()
  ,shouldComponentUpdate(), render(), getSnapshotBeforeUpdate(), componentDidUpdate()

- Unmounting gồm có phưong thức componentWillUnmount(): phương thức được gọi trước khi remove component khỏi DOM
