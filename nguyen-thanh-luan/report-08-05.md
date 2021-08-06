# NGUYỄN THÀNH LUÂN - Report 08/05:

# Day 3.

**Callback** 
- Callback: là 1 hàm được truyền qua đối số của function khác.

```js
    function myFunction(myInfo){
      myInfo('Nguyễn Thành Luân');
    }
    function myCallback(value){
      console.log(value);
    }
    myFunction(myCallback);
    // Run => Nguyễn Thành Luân
```

- Khi các hàm callback lồng nhau quá nhiều có thể dẫn đến tình trạng callback hell.

```js
    function myFunction(myInfo){
      setTimeout(function(){
        myInfo('Nguyen Thanh Luan');
        setTimeout(function(){
          myInfo('28');
          setTimeout(function(){
            myInfo('Hà Nội')
          },6000)
        },5000)
      },2000)  
    }
    function myCallback(value){
      console.log(value);
    }
    myFunction(myCallback);
```	
- Để xử lý callback hell ta có thể chia các callback thành nhiều phần để phần trước sẽ gọi phần sau hoặc dùng Promise.

**Array**
- Array: là 1 biến đặc biệt có thể chứa nhiều giá trị cùng 1 lúc.

```js
    const myArray = [item1, item2, .....]; // tạo mảng
```
- Trong Array có rất nhiều phương thức:
```js
  const myArr = [2,4,3,1,9,8];
  myArr.sort();
  console.log(myArr); // Run => [1,2,3,4,8,9]
  // sort(): sắp xếp mảng theo thứ tự nhỏ đến lớn

  myArr.reverse();
  console.log(myArr); // Run => [8,9,1,3,4,2]
  // reverse(): sắp xếp mảng theo chiều ngược lại

  const animals = ['Cat', 'Dog', 'Fish', 'Bird'];
  console.log(animals.toString()); // Run => Cat,Dog,Fish,Bird
  // toString(): chuyển đổi mảng thành chuỗi

  console.log(animals.join('*')); // Run => Cat*Dog*Fish*Bird
  // join(): cũng giống toString() nhưng có thể chỉ định được dấu phân cách

  animals.pop(); 
  console.log(animals); // Run => ['Cat', 'Dog', 'Fish']
  // pop(): xóa bỏ phần tử cuối cùng của mảng
  
  animals.push('Snake');
  console.log(animals); // Run => ['Cat', 'Dog', 'Fish', 'Bird', 'Snake']
  // push: thêm phần từ vào vị trí cuối mảng

  animals.shift();
  console.log(animals); // Run => ['Dog', 'Fish', 'Bird']
  // shift(): xóa phần tử đầu tiên của mảng

  animals.unshift('Snake');
  console.log(animals); // Run => ['Snake', 'Cat', 'Dog', 'Fish', 'Bird']
  // unshift(): thêm phần từ vào vị trí đầu tien của mảng

  animals.splice(2,0,'Snake', 'Chicken'); // 2- vị trí bắt đầu thêm. 0- số phần tử trong mảng bị xóa
  console.log(animals); // Run => ['Cat', 'Dog', 'Snake', 'Chicken', 'Fish', 'Bird']
  // splice(): trả về mảng mới.

  const myAnimals = animals.concat('Snake')
  console.log(myAnimals); // Run => ['Cat', 'Dog', 'Fish', 'Bird', Snake]
  // concat(): nối mảng

  const myAnimals = animals.slice(2); // 2 - vị trí bắt đầu cắt mảng
  console.log(myAnimals); // Run => ['Fish', 'Bird',]
  // slice(): tạo ra mảng mới bắt đầu từ mảng ban đầu
```

**Multidimensional Arrays**
- Mảng đa chiều: là 1 biến đặc biệt có thể chứa nhiều mảng trong đó
```js
  let activities = [
    ['Work', 9],
    ['Eat', 1],
    ['Commute', 2],
    ['Play Game', 1],
    ['Sleep', 7]
];
```

- Mảng đa chiều: cũng có những phương thức giống màng 1 chiều.
```js
  activities.push(['Play Sport', 1])
  console.table(activities);
    ┌─────────┬──────────────┬───┐
    │ (index) │      0       │ 1 │
    ├─────────┼──────────────┼───┤
    │    0    │    'Work'    │ 9 │
    │    1    │    'Eat'     │ 1 │
    │    2    │  'Commute'   │ 2 │
    │    3    │ 'Play Game'  │ 1 │
    │    4    │   'Sleep'    │ 7 │
    │    5    │ 'Play Sport' │ 1 │
    └─────────┴──────────────┴───┘
  .....
```

**Access and Iterate Through an Array**
- Để truy cập và lặp lại trong 1 mảng ta có rất nhiều phương thức.
- forEach(): Duyệt qua từng phần tử của mảng
- every(): kiếm tra các phần tử trong mảng có thỏa mãn điều kiện hay không. 1 phần tử sai là false
- some(): giống every() nhưng chỉ cần 1 phần tử thỏa mãn điều kiện là được
- filter(): Lọc mảng ra tập hợp các phần tử có tiêu chí cụ thể.
- find(): giống filter() nhưng trả về 1 phần tử
- map(): tạo mảng mới dựa trên mảng ban đầu nhưng không thay đổi mảng gốc.
- reduce():


```js
  const infoPerson = [
   {
      name: 'Luan',
      age: 28,
      sex: 'Male'
  },
  {
      name: 'An',
      age: 18,
      sex: 'Male'
  },
  {
      name: 'Lan',
      age: 25,
      sex: 'Female'
  }
];

  infoPerson.forEach(function(info){
      console.log(info); 
   /* 0 { name: 'Luan', age: 28, sex: 'Male' }
      1 { name: 'An', age: 18, sex: 'Male' }
      2 { name: 'Lan', age: 25, sex: 'Female' } */
  });
  var infoMale = infoPerson.every(function(value, index) {
      return value.sex === 'Male';
  });
  console.log(infoMale); // Run => false
  // Kiểm tra tất cả infoPerson.sex, nếu có 1 trường hợp khác 'Male' thì false
  // some(): giống every nhưng chỉ cần 1 thỏa mãn 1 điều kiện là true

  var infoAge = infoPerson.find(function(value, index) {
      return value.age == 25;
  });
  console.log(infoAge);
  // Kiểm tra xem có infoPerson.age = 25 => Run: { name: 'Lan', age: 25, sex: 'Female' }
  // filter(): giống find() nhưng trả ra tất cả phần tử thỏa mãn

  var newArry = infoPerson.map(function(value){
    return {
      name: 'Tên tôi là' + value.name,
      age: value.age,
      sex: value.sex
    };
  })
  console.log(newArry);
  // tạo ra mảng mới và thêm chuỗi 'Tên tôi là' trước trường 'name'

