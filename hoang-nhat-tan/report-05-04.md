# Redux thunk

- Redux thunk là một middleware cho phép viết các Action trả về một function thay vì một plain javascript object bằng cách trì hoãn việc đưa action đến reducer.
- Redux thunk được sử dụng để xử lý các logic bất đồng bộ phức tạp cần truy cập đến store hay là việc lấy dữ liệu get API

```js
	export const selectedItem = item =>{
		return{
			type: "SELECTED_ITEM",
			payload: item
		};
	};
```

* ở đây action trả về một plain javascript objec

```js
	export const selectedItem = item =>{
		const res = await dataItems.get('/items');
		return{
			type: "GET_ITEMS",
			payload: response
		};
	};
```
* Action trả về một response API