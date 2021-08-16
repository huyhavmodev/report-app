# NGUYỄN THÀNH LUÂN - Report 08/16:

**ReactJS**

**State**
- State: là một object có thể được sử dụng để chứa dữ liệu hoặc thông tin về components. State có thể được thay đổi bất cứ khi nào mong muốn.
    + Ta có thể truyền props sang các components khác nhau nhưng state chỉ tồn tại trong phạm vi của components chứa nó.
    + Mỗi khi state thay đổi thì components đó sẽ được render lại.
```js
    // Khởi tạo state
    this.setState = {
        name: 'LuanNT' 
        }
    // thay đổi state
    this.setState = ({
        name: 'newName'
        })
```
- Counter App dùng Class Component: https://codesandbox.io/s/musing-mccarthy-pk79n


**Lifecycle**
- Lifecycle: 3 giai đoạn
    + Mounting: giai đoạn bắt đầu sẽ khởi tạo props và state bên trong thông qua phương thức constructor
        . componentWillMount(): Được khởi chạy khi một component chuẩn bị được mount (tức là trước khi thực hiện render)
            . Khi thực hiện xong componentWillMount() thì component mới có thể được mount. (không nên thay đổi props, state hay call API ở hàm này).
        . componentDidMount(): Được gọi khi component đã được mount (render thành công )
            . Trong componentDidMount() có thể thay đổi props, state hoặc call API.

    + Updating: dữ liệu (props & state) sẽ được cập nhật để đáp ứng với các sự kiện của người dùng.
        . shouldComponentUpdate(): Phương thức này xác định xem component có nên được render lại hay không?
            . Mặc định nó trả về true. Nhưng bạn có thể thay đổi giá trị trả về của nó theo từng trường hợp.
            . Nhận về 2 tham số truyền vào là nextState và nextProps.
        . componentWillUpdate(): Phương thức này được gọi trước khi tiến hành re-render.
            . Thực hiện các hành động như update state, props,...trong phương thức này trước khi tiến hành re-render.
            . Nhận vào 2 tham số đó là nextState và nextProps.
        . componentDidUpdate(): được gọi khi component đã re-render xong

    + Unmounting: khi tất cả các tác vụ hoàn thành và bạn tiến hành unmount DOM.
        . componentWillUnmount():

**Handling Events**
- Handling Events - Xử lý sự kiện:
    + Các sự kiện React được đặt tên bằng camelCase, thay vì chữ thường. Ví dụ: onclick -> onClick, onchange -> onChange.
    + Với JSX: ta truyền một hàm để bắt sự kiện, thay vì một chuỗi như HTML thông thường.
```js
    /// HTML
    <button onclick="changeName()">Change Name</button>

    // JSX
    <button onClick={changeName}>Change Name</button>
```
- Không thể return false để chặn hành động mặc định được, ta phải sử dụng preventDefault().

**Conditional Rendering**
- Trong React JS chúng ta tạo ra các components riêng biệt, vì vậy ta có thể chỉ định các thành phần nào được render bằng việc sử dụng biểu thức điều kiện.
```js
    if(condition)
    {
        return(
            <div>
                ...
            </div>
        )
    }
    else {
        return(
            <div>
                ...
            </div>
        )
    }
```

**List and Key**
- List: khởi tạo list trong React JS tương tự như khởi tạo list trong Javascript.
- Khi các lists này có nhiều items thì React rất khó có thể kiểm soát được items => Cần chỉ định cho nó một key để định danh.
    + Các keys này là duy nhất, các keys này không được trùng lặp trong các lists.
```js
    function List(props) {
    const myList = [
        {
          id : 'r',
          name : 'ReactJS'
        },
        {
          id : 'a',
          name : 'AngularJS'
        },
        {
          id : 'v',
          name : 'VueJs'
        },
      ]
     
      //Thêm thuộc tính key vào trong thẻ jsx
      const listItems = myList.map((item) =>
        <li key = {item.id}>{item.name}</li>
      );
     
      return (
        <ul>{listItems}</ul>
      );
  }
export default List;
```

**Form**
- Các thao tác với form:
    + Lấy giá trị input: bắt sự kiện onChange của input.
    + Sau khi lấy giá trị input cần submitForm: bắt sự kiện onSubmit trong form.
    + Validation Form: kiểm tra dữ liệu nhập vào form.
- Tạo form đăng nhập cơ bản: https://codesandbox.io/s/suspicious-cache-oqfk9

**Lifting State Up**
- Kỹ thuật lifting state up là cách mà có thể chia sẻ dữ liệu cho các component khác. 
- Khi bạn thay đổi dữ liệu của 1 component con thì bạn sẽ gửi dữ liệu cho component cha biết.