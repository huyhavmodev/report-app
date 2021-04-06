# Nguyen Tien Manh - 04/06

## TOPIC: High-Order Component (HOC)

- HOC (Higher Order Component) đơn giản là một component nhận đầu vào là một component và trả về là một component khác.
- HOC giúp chúng ta tránh việc lặp code và sử dụng lại logic cho nhiều component khác nhau.
- HOC không chỉnh sửa component ban đầu(Wrapper Component) mà nó chỉ bọc component gốc trong một Container. Sau đó nó sẽ truyền thêm một số data, props xuống cho Wrapped Component.
- HOC nên là một pure function nên nó không được phép chỉnh sửa input, và không có side-effect.
- Ví dụ về HOC: 
  - Có 2 component ViewCategory và Viewpost
  - 2 component này đều dùng chung logic để fetch data ra hiển thị
  - Thay vì phải viết logic hiển thị ở trong từng component
  => Sử dụng HOC để xử lý vấn đề trên
- ViewCategory component
```javascript
export default function ViewCategory(props) {
    return (
        <div>
            <h1>View Category</h1>
            <p>ID: {props.data.id}</p>
            <p>Name: {props.data.name}</p>
        </div>
    )
}
```
- ViewPost component
```javascript
export default function ViewPost(props) {
    return (
        <div>
            <h1>View Post</h1>
            <p>ID: {props.data.id}</p>
            <p>Name: {props.data.name}</p>
            <p>Content: {props.data.content}</p>
        </div>
    )
}
```
- HOC
```javascript
export function withData(WrappedComponent, fetchData) {
    return class extends Component {
        constructor(props) {
            super(props);
            this.state = {
                data: {}
            }
        }

        componentDidMount() {
            this.setState({
                data: fetchData(this.props)
            })
        }

        render() {
            return (
                <WrappedComponent data={this.state.data} {...this.props} />
            )
        }
    }
}
```
- Sử dụng
```javascript
function App() {
  const ViewCategoryData = withData(ViewCategory, (props) => Datasource.getCategory(props.id));
  const ViewPostData = withData(ViewPost, (props) => Datasource.getPost(props.id));
  return (
    <div className="App">
      <ViewCategoryData id={10} />
      <ViewPostData id={100} />
    </div>
  );
}
```