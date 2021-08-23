**State**

- State: là một object có thể được sử dụng để chứa dữ liệu hoặc thông tin về components.
  - State có thể thay đổi theo ý muốn nhưng không được thay đổi trực tiếp mà phải dùng setState().
  - Ta có thể truyền props sang các components khác nhau nhưng state chỉ tồn tại trong phạm vi của components chứa nó.
  - Mỗi khi state thay đổi thì components đó sẽ được render lại.
  - Nhiều lệnh setState() sẽ được React gom lại vào thành một lần update để tối ưu hiệu năng
  -

**Lifecycle**

- Lifecycle: 3 giai đoạn

  - Mounting: giai đoạn bắt đầu sẽ khởi tạo props và state bên trong thông qua phương thức constructor
    . componentWillMount(): Được khởi chạy khi một component chuẩn bị được mount (tức là trước khi thực hiện render)
    . Khi thực hiện xong componentWillMount() thì component mới có thể được mount. (không nên thay đổi props, state hay call API ở hàm này).
    . componentDidMount(): Được gọi khi component đã được mount (render thành công )
    . Trong componentDidMount() có thể thay đổi props, state hoặc call API.

  - Updating: dữ liệu (props & state) sẽ được cập nhật để đáp ứng với các sự kiện của người dùng.
    . shouldComponentUpdate(): Phương thức này xác định xem component có nên được render lại hay không?
    . Mặc định nó trả về true. Nhưng bạn có thể thay đổi giá trị trả về của nó theo từng trường hợp.
    . Nhận về 2 tham số truyền vào là nextState và nextProps.
    . componentWillUpdate(): Phương thức này được gọi trước khi tiến hành re-render.
    . Thực hiện các hành động như update state, props,...trong phương thức này trước khi tiến hành re-render.
    . Nhận vào 2 tham số đó là nextState và nextProps.
    . componentDidUpdate(): được gọi khi component đã re-render xong

  - Unmounting: khi tất cả các tác vụ hoàn thành và bạn tiến hành unmount DOM.
    . componentWillUnmount():
