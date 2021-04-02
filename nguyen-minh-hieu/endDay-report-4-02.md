## Nguyen Minh Hieu - 04/02

### Topic: Async/Await trong Javascript

#### 1. Async/Await là gì?

- Async/Await là 1 cơ chế thực hiện các tác vụ bất đồng bộ 1 cách tuần tự. Các cách làm việc với code bất đồng bộ là sử dụng callback và promise.
- Async/Await được xây dựng dựa trên promise. Do đó nó không thể sử dụng với callback

- Async/Await làm cho code bất đồng bộ nhìn và chạy như code đồng bộ.
#### Async
- Async được dùng để khai báo 1 hàm bất đồng bộ và nó trả về 1 promise 

#### Await
- Await dùng để đợi 1 Promise cho đến khi nó trả về kết quả.
- nó chỉ có thể được sử dụng bên trong Async block
#### Cú phát Async/Await
1. Async
- Từ khoá Async được đặt trước 1 hàm làm cho hàm trả về promise
ví dụ:
``` javascript
async function myFunction() {
  return Promise.resolve("Hello");
}
```
2. Await
- Từ khoá Await được đặt trước 1 hàm làm cho hàm chờ 1 promise
```javascript
async function asyncFunction() {
  var y = await 20;
  console.log(y); // 20
}
asyncFunction();
```
#### xử lý lỗi với Async/Await
- khi promise bị reject chúng ta có thể dùng try…catch để xử lý lỗi 

```javascript
async function f() {

  try {
    let response = await fetch('http://no-such-url');
  } catch(err) {
    alert(err); // TypeError: failed to fetch
  }
}

f();
```
#### Tại sao nên dùng Async/Await?
1. Ngắn gọn
2. Câu lệnh điều kiện
ví dụ khi dùng với promise

```javascript
const makeRequest = () => {
  return getJSON()
    .then(data => {
      if (data.needsAnotherRequest) {
        return makeAnotherRequest(data)
          .then(moreData => {
            console.log(moreData)
            return moreData
          })
      } else {
        console.log(data)
        return data
      }
    })
}
```

Khi dùng với async/await

```javascript
const makeRequest = async () => {
  const data = await getJSON()
  if (data.needsAnotherRequest) {
    const moreData = await makeAnotherRequest(data);
    console.log(moreData)
    return moreData
  } else {
    console.log(data)
    return data    
  }
}
```