# Nguyen Tien Manh - 04/02

## TOPIC: ImmerJS

- Đối với React Redux thì việc cập nhập làm mới lại store với những state đơn giản thì việc này không mất quá nhiều thời gian, nhưng với những state có cấu trúc là object phức tạp nhiều lớp thì việc này rất tốn thời gian.    
    =>  Immer sẽ giúp cải thiện điều này, giúp chúng ta cập nhật lại state một cách đơn giản và dễ dàng hơn.
- Immer là một package nhỏ cho phép bạn làm việt với các object bất biến một cách tiện lợi.
    - Thực hiện tất cả thay đổi trên một **draftState** tạm thời, đây là một proxy của **currentState**. Khi mà tất cả việt mutate xong xuôi thì Immer sẽ cho ra một **nextState** dựa trên những thay đổi trên **draftState**. Điều này đồng nghĩa với việc có thể tương tác với data một cách đơn giản mà vẫn giữ được tính bất biến của data.
- Produce: đây là hàm quan trọng nhất của Immer
    ```javascript
    import produce from "immer"
    const todos = [ /* 2 object todo ở đây*/ ]
    const nextTodos = produce(todos, draft => {
        draft.push({ text: "learn immer", done: true })
        draft[1].done = true
    })
    // state cũ không bị thay đổi
    console.log(todos.length)        // 2
    console.log(todos[1].done)       // false
    // state mới đã được thay đổi từ draft
    console.log(nextTodos.length)    // 3
    console.log(nextTodos[1].done)   // true
    // chia sẽ cấu trúc tham chiếu với nhau
    console.log(todos === nextTodos)       // false
    console.log(todos[0] === nextTodos[0]) // true
    console.log(todos[1] === nextTodos[1]) // false
    ```
- Đối với reducer
    - Spread operator
    ```javascript
    export const productReducer = (state = initialState, action) => {
    switch (action.type) {
        case 'ADD':
        return {
            ...state,
            products: [...state.products, action.payload],
        };
        case 'UPDATE':
        const _products = [...state.products];
        const index = _products.findIndex(
            (product) => product.id === action.payload.id
        );
        _products[index] = action.payload;
        return { ...state, products: _products };
        default:
        return state;
    }
    };
    ```
    - Khi dùng Immer (thay vì phải dùng spread operator thì chỉ cần bọc toàn bộ action trong produce và sử lý vs draftState)
    ```javascript
    import produce from 'immer';
    export const productReducer = (state = initialState, action) =>
    produce(state, (draft) => {
        switch (action.type) {
        case 'ADD':
            draft.products.push(action.payload);
            break;
        case 'UPDATE':
            const index = draft.products.findIndex(
            (product) => product.id === action.payload.id
            );
            draft.products[index] = action.payload;
            break;
        default:
            break;
        }
    });
    ```
    => Mọi thứ sẽ trông đơn giản và ngắn gọn hơn
- Nếu để ý thì khi dùng với produce chúng ta không cần return về một state mới trong switch case mà chỉ cần break thôi, vì việc return state mới đã có produce lo