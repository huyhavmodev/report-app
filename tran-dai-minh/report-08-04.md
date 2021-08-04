## TRAN DAI MINH 08-04

## TOPIC: Callback, Array, Multidimensional Arrays, Access and Iterate Through an Array.

- Callback: là **function** được truyền dưới dạng đối số, bên trong **function** để thực hiện hành động nào đó.

```
function greeting(name) {
  alert('Hello ' + name);
}

function processUserInput(callback) {
  var name = prompt('Please enter your name.');
  callback(name);
}

processUserInput(greeting);
// expected output: Hello + name.
```

- **Array** là một biến đặc biệt có thể chứa nhiều giá trị cùng một lúc.

```
const name = ['minh', 'hoa','dat'];
```

- **Multidimensional Arrays** là một biến có thể chứa nhiều **array** con bên trong.

```
const arr = [[1,2],[3,4],[5,6]]
```

- ccess and Iterate Through an Array

- Converting Arrays to Strings use tostring();

```
arr.toString();
```

- Popping and Pushing

- The pop() method removes the last element from an array.

```
var arr = [1, 2, 3, 4, 5];
arr.pop();
// expected output: [1,2,3,4,4]
```

- The push() method adds a new element to an array at the end.

```
var arr = [1, 2, 3];
arr.push(4);
// expected output: [1,2,3,4]
```

- The shift() method removes the first element from an array and returns that removed element. This method changes the length of the array.

```
const array1 = [1, 2, 3];
aarray1rr.shift();
// expected output: [2,3]
```

- The unshift() method adds one or more elements to the beginning of an array and returns the new length of the array.

```
const array1 = [1, 2, 3];

array1.unshift(4, 5);
// expected output: Array [4, 5, 1, 2, 3]
```

- The splice() method changes the contents of an array by removing or replacing existing elements and/or adding new elements.

```
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// expected output: Array ["Jan", "Feb", "March", "April", "June"]
```

- TThe concat() method is used to merge two or more arrays. This method does not change the existing arrays, but instead returns a new array.

```
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
```

- The slice() method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included) where start and end represent the index of items in that array. The original array will not be modified.

- The forEach() method calls a function (a callback function) once for each array element.

- The map() method creates a new array by performing a function on each array element. It does not execute the function for array elements without values. The original array will not to be changed.

```
const array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);
// expected output: Array [2, 8, 18, 32]
```

- The filter() method creates a new array with array elements that passes a test.

- The reduce() method runs a function on each array element to produce (reduce it to) a single value. It works from left-to-right in the array.

- The every() method check if all array values pass a test.

- The some() method check if some array values pass a test.

- The indexOf() method returns the first index at which a given element can be found in the array, or -1 if it is not present.

- The find() method returns the value of the first element in the provided array that satisfies the provided testing function.

- The findIndex() method returns the index of the first element in the array that satisfies the provided testing function. Otherwise, it returns -1, indicating that no element passed the test.
