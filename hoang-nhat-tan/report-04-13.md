# Day 5

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

- The concat() method creates a new array by merging existing arrays.

```js
	var arr1 = [1, 2, 3];
	var arr2 = [4, 5];
	var new_arr = arr1.concat(arr2);
```

- The slice() method slices out a piece of an array into a new array.The slice() method creates a new array. It does not remove any elements from the source array.

- The forEach() method calls a function (a callback function) once for each array element.

- The map() method creates a new array by performing a function on each array element. It does not execute the function for array elements without values. The original array will not to be changed.

```js
	var arr = [1, 3, 4, 7];
	var new_arr = arr.map(item, ()=>{
		item = item * 2
	});
```

- The filter() method creates a new array with array elements that passes a test.

- The reduce() method runs a function on each array element to produce (reduce it to) a single value. It works from left-to-right in the array.

- The every() method check if all array values pass a test.

- The some() method check if some array values pass a test.

- The indexOf() method searches an array for an element value and returns its position.

- The find() method returns the value of the first array element that passes a test function.

The findIndex() method returns the index of the first array element that passes a test function.

**Bubbling and capturing**

- When an event happens on an element, it first runs the handlers on it, then on its parent, then all the way up on other ancestors.

![alt text](https://viblo.asia/uploads/05f9f63c-eaed-496a-89da-f02eab6dff88.png)

- Stopping bubbling: We use event.stopPropagation()


# Day 1 + 2 Week II #

**Basic data structure 100%**

- Use an Array to store a collection of Data
- Access an Array's Contents Using Bracket Notation
- Add Items to an Array with push() and unshift()
- Remove Items from an Array with pop() and shift()
- Remove Item using splice()
- Add Items using splice()
- Copy Array Items using slice()
- Iterate through all an Array's Item using For Loops
- Access property with bracket and dot notation

**Basic Algorithm scripting 60%**

- Convert Celsius to Fahrenheit
- Reverse a String
- Factorialize a Number
- Find the Longest Word in a String
- Return Largest Numbers in Arrays
- Confirm the Ending
- Repeat a String Repeat a String
- Truncate a String
- Finders Keepers

