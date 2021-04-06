# API - sử dụng với axios

1. Vì sao sử dụng axios?

- dễ sử dụng, nhiều tính năng

2. Cài đặt

   > npm install axios

3. Áp dụng trong react

- Có thể dùng trực tiếp hoặc tạo 1 instance của api cho dễ quản lí

- Tạo 1 folder tên: apis
- tạo 1 file instance của api (ví dụ sử dụng api jsonPlaceholder)

  ```javascript
  // src/apis/jsonPlaceholder.js
  import axios from "axios";

  export default axios.create({
    // tạo base url trước để tí sử dụng
    baseURL: "https://jsonplaceholder.typicode.com",
    // anothor options...
  });
  ```

- sử dụng instance vừa đc tạo khi cần:

  ```javascript
    // src/actions/index.js
    // sử dụng thêm thunk
    import jsonPlaceholder from '../apis/jsonPlaceholder'

    export const createAnAction () => async (dispatch) => {
      // lay posts tu api,
      // không cần điền đầy đủ url vì đã tạo instance với baseURL
      const respone = await jsonPlaceholder.get('/posts');
      dispatch({
        type: "SOMETYPE",
        payload: respone.data
      });
    }
  ```
