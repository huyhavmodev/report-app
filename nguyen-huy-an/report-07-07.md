# Nguyen Huy An - 07/07

## Access and Iterate Through an Array

- There are some way to access and iterate an Array
### What: 
- Using for loop
- Using while loop
- Using forEach method
- Using every method
- Using map

+ Using forEach:
    ```javascript
   const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
   let sum = 0;
    forEach(numbers, function(element){
    sum += element;
});
   console.log(sum);
    ```
+ Array supported forEach with the structure: 

    ```javascript
  arr.forEach(function callback(currentValue, index, array) {
    // your iterator
}[, thisArg]);
    ```

+ Using map method:

```javascript
index = 0;
array = [ 1, 2, 3, 4, 5, 6 ];
  
square = x => Math.pow(x, 2);
squares = array.map(square);
console.log(array);
console.log(squares);

//Output:
//1 2 3 4 5 6 
//1 4 9 16 25 36

```
```javascript
index = 0;
array = [ 1, 2, 3, 4, 5, 6 ];
  
const under_five = x => x < 5;
  
if (array.every(under_five)) {
    console.log('All elements are less than 5');
}
else {
    console.log('At least one element is not less than 5');
}
```
## Data Structure
- There are some common types of data structure:
    + Array: an ordered list of values, or a collection of elements (values or variables) identified by an index or key
    + Linked list: a sequence of data structures with each node consisting of 2 pieces of info: node's data and reference to the next node in the chain
    + Queue: work on the principle FIFO
    + Stack: work on the principle LIFO
    

