# Sử dụng thư viện reselect trong redux

> reselect ghi nhớ giá trị giữa các lần render, dùng để giảm thiểu tính toán, trích xuất thông tin từ redux store mỗi khi state tree thay đổi. Từ đó làm tăng hiệu suất app

# Demo: (ví dụ trong reselect npm)

## Vấn đề:

**todos** sẽ được tính toán lại mỗi lần state trong redux store thay đổi. Nếu phải tính toán nhiều hoặc state tree nhiều sẽ dẫn đến giảm hiệu suất

```javascript
import { connect } from "react-redux";
import { toggleTodo } from "../actions";
import TodoList from "../components/TodoList";

// tạo các function "selector" để trích xuất các thành phần trong state khi đưa vào mapStateToProps hoặc useSelector hook
const getVisibleTodos = (todos, filter) => {
  switch (filter) {
    case "SHOW_ALL":
      return todos;
    case "SHOW_COMPLETED":
      return todos.filter((t) => t.completed);
    case "SHOW_ACTIVE":
      return todos.filter((t) => !t.completed);
  }
};

// sử dụng trong mapStateToProps
const mapStateToProps = (state) => {
  return {
    todos: getVisibleTodos(state.todos, state.visibilityFilter),
  };
};

const mapDispatchToProps = (dispatch) => {
  return {
    onTodoClick: (id) => {
      dispatch(toggleTodo(id));
    },
  };
};

const VisibleTodoList = connect(mapStateToProps, mapDispatchToProps)(TodoList);

export default VisibleTodoList;
```

## Giải pháp:

sử dụng hàm createSelector của reselect:

```javascript
import { createSelector } from "reselect";

// selector fn để lấy thông tin filter + todos list
const getVisibilityFilter = (state) => state.visibilityFilter;
const getTodos = (state) => state.todos;

// sử dụng createSelector
// đưa các selectors trên vào tham số đầu trong mảng, (hoặc viết lần lượt cách nhau dấu phẩy)
// giá trị các selectors trên được truyền lần lượt như là đối số hàm cuối cùng
// hàm cuối cùng để tính toán giá trị cần lấy cuối cùng.
export const getVisibleTodos = createSelector(
  [getVisibilityFilter, getTodos],
  (visibilityFilter, todos) => {
    switch (visibilityFilter) {
      case "SHOW_ALL":
        return todos;
      case "SHOW_COMPLETED":
        return todos.filter((t) => t.completed);
      case "SHOW_ACTIVE":
        return todos.filter((t) => !t.completed);
    }
  }
);

const mapStateToProps = (state) => {
  todos: getVisibleTodos(state);
};
```

## Note: Khi sử dụng tham số thứ 2 ownProps trong mapStateToProps thì function selector nên trả về createSelector:

```javascript
// 1. Tạo fn selector
const makeGetVisibleTodos = () => {
  // retrun createSelector,
  // không gán makeGetVisibleTodos = createSelector()
  return createSelector(
    [getVisibilityFilter, getTodos],
    (visibilityFilter, todos) => {
      switch (visibilityFilter) {
        case "SHOW_COMPLETED":
          return todos.filter((todo) => todo.completed);
        case "SHOW_ACTIVE":
          return todos.filter((todo) => !todo.completed);
        default:
          return todos;
      }
    }
  );
};

// 2. Sử dụng với mapStateToProps
const makeMapStateToProps = () => {
  const getVisibleTodos = makeGetVisibleTodos();
  const mapStateToProps = (state, props) => {
    return {
      todos: getVisibleTodos(state, props),
    };
  };
  return mapStateToProps;
};

// connect
const VisibleTodoList = connect(makeMapStateToProps)(TodoList);
```
