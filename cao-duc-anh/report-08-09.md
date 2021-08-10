**8 cấu trúc dữ liệu thường dùng**
- Array: là 1 biến đặc biệt chứa nhiều dữ liệu cùng 1 lúc.
    + Phần tử: các mục được lưu giữ trong mảng là 1 phần tử
    + Index: mỗi vị trí của 1 phần tử trong mảng có 1 chỉ mục được sử dụng để nhận diện phần tử
    + Array thường có các bài toán liên quan đến sắp xếp và tìm kiếm, tìm các phần tử chẵn lẻ, số lần xuất hiện của các phần tử.

- Linked List: mỗi phần tử trong Linked List sẽ có 1 con trỏ, trỏ tới phần tử phía sau nó, khi muốn thêm phần tử ta chỉ việc cho phần tử cuối (tail) trỏ tới phần tử mới.
    + Linked list được dùng khi lưu trữ một danh sách có số lượng phần tử không có định, cần thêm và xoá phần tử.
    + Linked list có 2 biến thể là Single-linked và Double-linked. Với Double-linked, thì 1 phần tử sẽ lưu 2 con trỏ, trỏ về phía trước và phía sau.

- Stack: cho phép thêm 1 phần tử lên đầu stack(push) và lấy phần tử trên đầu stack ra(pop). Các phần tử vào sau sẽ được ra trước nên gọi là Last In First Out(LIFO)
- Queue thì ngược lại, cho phép thêm 1 phần tử vào queue, lấy 1 phần tử ra khỏi queue. Các phần tử nào vào trước sẽ được ra trước nên được gọi là First In First Out(FIFO).
    + Hai cấu trúc dữ liệu này cho phép thêm/xoá các phần tử dựa theo thứ tự đưa vào.
    + Ứng dựng: Stack được dùng để implement chức năng Undo/Redo, chức năng Go Back/Go Next trên trình duyệt. Queue dùng để implement message queue cho phép các thành phần trong 1 hệ thống trao đổi thông tin.

- Hash table: Khi đưa 1 phần tử vào Hash Table, phải chỉ định 1 key (ví dụ lưu nhân viên thì sẽ có ID nhân viên). Khi cần truy cập 1 phần tử từ Hash Table thì dựa theo key.

- Set: là một tập hợp các phần tử không theo thứ tự mà mỗi phần tử trong đó không được trùng nhau. Do đặc tính lưu các phẩn tử không trùng nhau, set thường được dùng để lưu trữ các IP/các trang web đã truy cập.

- Graph: Đồ thì là một tập hợp nhiều điểm, các điểm này nối với nhau bằng các cạnh.

- Tree: cũng là một dạng đồ thị, 1 tree sẽ có node gốc (root), mỗi node sẽ có 1 hoặc nhiều node con, những node nào không có node con được gọi là leaf note. 
    + Tree có 2 biến thể phổ biến, được dùng nhiều là: Binary tree, mỗi node sẽ có tối đa 2 con, được gọi lần lượt là node trái và node phải. Binary search tree: Biến thể của Binary Tree. Các phần tử trong subtree bên trái phải nhỏ hơn node giữa, bên phải phải lớn hơn node giữa. Mỗi cây con của cây phải là Binary Search Tree

**PROMISE, ASYNC AWAIT**

    Promise là một JS Object để link producing code và comsuming code.
```js
   //PROMISE
let is_shop_open = true;

let order = (time, work) => {

    //Một promise được khởi tạo với function có câu lệnh resolve và reject
    return new Promise( (resolve, reject) => {

        if(is_shop_open) {
            
            setTimeout(() => {
                resolve( work() )
            }, time)
            
        } else {
            reject( console.log("Our shop is closed") )
        }
     })
}

order(2000, () => console.log(`${stocks.Fruits[0]} was selected`))

.then(() => {
    return order(0000,() => console.log('production has started'))
})

.then(() => {
    return order(2000,() => console.log("The fruit has been chopped"))
})

.then(() => {
    return order(1000,() => console.log(`Add ${stocks.liquid[0]} and ${stocks.liquid[1]}`))
})

.then(() => {
    return order(1000,() => console.log("Start the machine"))
})
.then(() => {
    return order(2000,() => console.log(`Selected ${stocks.holder[0]} as Container`))
})
.then(() => {
    return order(3000,() => console.log(`Selected ${stocks.toppings[0]} and ${stocks.toppings[1]} as toppings`))
})
.then(() => {
    return order(2000,() => console.log("Serve Ice cream"))
})

.catch(() => {
    console.log("Customer left")
})

.finally(() => {
    console.log("End of the day");
    console.log("Shop closed");
})

function toppings_choice () {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve( console.log("Which topping would you love?") )
        }, 3000)
    })
}
```
    ES2017 giới thiệu async và await, giúp promise trông đơn giản hơn, tránh được chain .then() dài như trên.
    Từ khoá async sẽ thông báo rằng function sẽ xử lý bất đồng bộ và await sẽ được dùng để báo chúng ta muốn đợi kết quả của thao tác bất đồng bộ trong một function có đánh dấu async.
    Lưu ý: chỉ có thể dùng await khi đã khai báo async

    Syntax: thêm keyword async trước bất kỳ function bình thường nào sẽ biến nó thành promise.

```js
function time(ms) {
    return new Promise( (resolve, reject) => {
        if(is_shop_open) {
            setTimeout(resolve,ms);
        } else {
            reject(console.log("Shop is closed"))
        }
    });
}

async function kitchen() {
    try{
        
        await time(2000)
        console.log(`${stocks.Fruits[0]} was selected`)

        await time(2000)
        console.log("Fruit has been chopped")

        await time(1000)
        console.log(`Add ${stocks.liquid[0]} and ${stocks.liquid[1]}`)

        await time(1000)
        console.log("Start the machine")

        await time(2000)
        console.log(`Selected ${stocks.holder[0]} as the container`)

        await time(3000)
        console.log(`Selected ${stocks.toppings[0]} and ${stocks.toppings[1]} as toppings`)

        await time(2000)
        console.log("Serve Ice Cream")
    } 

    catch(error) {
        console.log("Customer left", error);
    }

    finally{
        console.log("Day ended, shop closed")
    }
}

kitchen();
```
