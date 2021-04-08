# Nguyen Tien Manh - 04/07

## TOPIC: Debounce, throttle

- Làm thế nào có thể ngăn chặn một function được gọi quá nhanh hoặc quá nhiều lần liên tiếp ?
- Nếu có một sự kiện như onClick hoặc onScroll và muốn ngăn hàm callback gọi lại quá nhanh, thì có thể giới hạn tốc độ thực hiện hàm callback. Điều này có thể được thực hiện bằng cách sử dụng
# Debounce 
- Debounce đảm bảo rằng một hàm sẽ không được thực thi sau một khoảng thời gian nhất định kể từ khi nó được gọi lần cuối. Điều này có thể hữu ích khi bạn phải thực hiện một số tính toán phức tạp để đáp ứng với một sự kiện có thể gửi đi nhanh chóng (ví dụ: các sự kiện scroll hoặc bàn phím).
- Ví dụ dưới đây nhập văn bản với độ trễ 250ms.
```javascript
import debounce from 'lodash.debounce';

class Searchbox extends React.Component {
  constructor(props) {
    super(props);
    this.handleChange = this.handleChange.bind(this);
    this.emitChangeDebounced = debounce(this.emitChange, 250);
  }

  componentWillUnmount() {
    this.emitChangeDebounced.cancel();
  }

  render() {
    return (
      <input
        type="text"
        onChange={this.handleChange}
        placeholder="Search..."
        defaultValue={this.props.value}
      />
    );
  }

  handleChange(e) {
    this.emitChangeDebounced(e.target.value);
  }

  emitChange(value) {
    this.props.onChange(value);
  }
}
```
# Throttle
- Throttle ngăn chặn một function được gọi nhiều lần trong một khung thời gian nhất định. 
- Ví dụ dưới đây điều chỉnh một sự kiện xử lý “click” để ngăn chặn việc gọi nó nhiều hơn một lần mỗi giây.
```javascript
import throttle from 'lodash.throttle';

class LoadMoreButton extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
    this.handleClickThrottled = throttle(this.handleClick, 1000);
  }

  componentWillUnmount() {
    this.handleClickThrottled.cancel();
  }

  render() {
    return <button onClick={this.handleClickThrottled}>Load More</button>;
  }

  handleClick() {
    this.props.loadMore();
  }
}
```