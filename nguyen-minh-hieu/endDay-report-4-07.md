## Nguyen Minh Hieu - 04/07

### Topic: Components and Props, State trong ReactJs

#### 1. Components là gì?

- là 1 khối code độc lập, có thể tái sử dụng , nó đại diện cho những thành phần riêng biệt trên giao diện người dùng
- Components giúp chúng ta chia UI nhiều phần nhỏ riêng biệt để dễ quản lý và tái sử dụng nhiều lần, dễ đọc, dễ viết 

- React có 2 loại Components: Function Components và Class Components

#### 1.1 Functional (Stateless) Components
- Function Components là 1 javascript function nó 1 props (viết tắt của properties) làm tham số và trả về 1 React element 

``` javascript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

- Mở rộng: Functional components cũng được nói với một cái tên là stateless components bởi vì chúng ta không thể làm nhiều thứ phức tạp như quản lý React State (data) hoặc phương thức life-cycle trong functional components.

Tuy nhiên, React giới thiệu React Hooks trong versions 16.8, giờ nó cho phép chúng ta sử dụng state và những features khác trong functional components.

#### 1.2 Class (Stateful) Components
- Class Componets là những class ES6
- Chúng phức tạp hơn functional components ở chỗ nó còn có: phương thức khởi tạo, life-cycle, hàm render() và quản lý state (data). Ví dụ dưới đây là class component:

``` javascript
    import React, {Component} from 'react';
    class DemoComponent extends Component {
        render () {
            return (
                <div> day chi la Demo thui</div>
            );
        }
    }
    export default DemoComponent;
```

- React class component là 1 class ES6, nó sẽ là 1 component khi nó kế thừa React component
- nó có thể nhận props và có thể maintain data của nó với state
- nó phải có method render() và trả về 1 react element
#### gọi 1 Component như thế nào 
- 1 Component đc gọi như 1 thẻ HTML nhưng chỉ khác là chúng sẽ bắt đầu bằng chữ hoa theo kiểu PascalCase.
```
<DemoComponent/>
```

#### 2. Props
- Props chính là properties của một component, chúng ta có thể thay đổi props bằng cách truyền dữ liệu từ bên ngoài vào. Props có thể là 1 object, funtion, string, number...
- Chú ý: Khi một props được truyền vào component thì nó là bất biến tức là dữ liệu của nó không được thay đổi 

#### 3. State
- State là biểu diễn trạng thái của Component, State là private chỉ có thể thay đổi state bên trong chính component đó
- Chúng ta có thể change states bằng cách gọi this.setState()

``` javascript
class App extends React.Component {
  constructor(props) {
    super(props)

    this.state = {
      name: 'your name'
    }
  }

  onChange(e) {
    this.setState({name: e.target.value});
  }

  render() {
    return (
      <div>
        <input type='text' onChange={this.onChange.bind(this)} />
        <Notification title="hello">{this.state.name}</Notification>
      </div>
    );
  }
}
```