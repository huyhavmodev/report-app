## Hoàng Văn Tùng - 08/06

### Day 5 (Continue)

**Array**

- Array are used to store multiple values in a single variable.

```js
	var arr_name = [item1, item2, ...];
```

**Multidimensional Arrays**

- Multidimensional Array is know as arrays inside another array. We need to put some arrays inside an array, then the total thing is working like a multidimensional array.

```js
	var multi_arr = [
					[item1, item2, item3],
					[item4, item5, item6],
					...
					]
```

**Access and Iterate Through an Array**

- Converting Arrays to Strings use tostring();

```js
	arr.toString();
```

- Popping and Pushing

- The pop() method removes the last element from an array.

```js
	var arr = [1, 2, 3, 4, 5];
	arr.pop()
```

- The push() method adds a new element to an array at the end.

```js
	var arr = [1, 2, 3];
	arr.push(4);
```

- The Shift() method removes the first array element and "shifts" all other elements to a lower index.

```js
	var arr = [1, 2, 3, 4, 5];
	arr.shift();
	// Removes the first element "1" from arr
```
 - The unshift() method adds a new element to an array at the beginning.

 ```js
	var arr = [1, 2, 3, 4, 5];
	arr.unshift(0);
	// add "0" at the beginning of arr and arr length + 1
```

- Deleting Elements

```js
	var arr = [1, 2, 3, 4, 5];
	delete arr[0];
	// Changes the first element in arr to undefined
```

- The splice() method can be used to add new items to an array.

```js
	var fruits = ["Banana", "Orange", "Apple", "Mango"];
	fruits.splice(2, 2, "Lemon", "Kiwi");

// The first parameter(2) defines the position where new element should be added
// The second parameter(2) defines how many elements should be removed
//The rest of the parameters ("Lemon" , "Kiwi") define the new elements to be added.
```
