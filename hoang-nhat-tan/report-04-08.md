# Day 1 + 2

**Hoisting**

	Hoisting is a Javascript mechanism where variables and function declarations are moved to top of their scope before code execution, same with the function.
```js
	function hoisting (){
		console.log(a);
	 	var a = "Hello world!"
	}
	 ///Result: undefined
```
	*Because The variable declaration is hoist in the top of function, but the initialise is not change*

**Scope and Closure**

	- Scope: When we declare a variable in a function, we can only access it in the function. These variable are call to be scoped to the function. There are 2 types of scopes in javascript: Global scope(block scope) and local scope(function scope)
	- Closure: If we define any inner function within another function, this inner function is called a closure. It retains access to the variables created in the outer function.
	*Example:*
```js
	var countNumbmer = (()=> {
		var counter = 0;
		return function() {
			counter += 1;
			return counter;
		}
	});
```

**Object, Prototype & Inheritance**

	- Object is collection of properties(an association between a name and a value)

	- Propotype: All objects inherit properties and methods from a prototype
	*Example*
```js
		function obj(x, y, z){
			this.x = x;
			this.y = y;
			this.z = z;
		}
		newObj = new obj(1, 2, 3);
```

	- Inheritance: It refers to an object's ability to access methods and other properties from another object. Objects can inherit things from other objects.
	*Example*
```js
		class Game{
			constructor(name){
				this.gameName = name;
			}
			get gname(){
				return this.gameName;
			}
			set gname(x){
				this.gameName = x;
			}
		}
		let newGame = new game("LOL");
```

**Condition statement**

	- Use if to specify a block of code to be executed, if a specified condition is true.
```js
	if(condition){
		...
	}
	else if{
		...
	}
	else{
		...
	}
```
	- Else to specify a block of code to be executed, if the same condition is false.
	- Else if to specify a new condition to test, if the first condition is false
	- Switch to specify manny alternative blocks of code to be executed

**Data type**

|   Data Types   |   Description                          		|   Example    |
|----------------|----------------------------------------		|--------------|
|String	         |Textual data                            		|'Hello world!'|
|Number          |An interger or a floating-point number  		|3; 3.14;...   |
|BigInt          |An interger with arbitrary precision    		|1n,...        |
|Boolean         |Any of two values: true or false        		| true & false |
|undefined       |A data type whose variable is not initialized | var x        |
|null 			 |Denotes a null value 							| let x = null;|
|symbol			 |Data type whose instance are unique are unique and immutable|
|object 		 | key-value pair of collection of data         |let game = {};|


**Immutable/Mutable, Pass by Value/Reference**

	- Mutable: data of Object can be change.

	- Immutable: data can't be change. When collection be created, it can't be change.Immutable provide user with a lot of stable data structures such as: Map(), List(), Set(), Size(), Delete(), Clear(),...



# Day 3 + 4

**this, apply, call, bind**

	- This: keyword refers to the object it belongs to:
		+ In a method, this refers to the owner object.
		+ Alone, this refers to the global object.
		+ In a function, this refers to the global object.
		+ In an event, this refers to the element that received the event.

	- bind(): The bind() function creates a new bound function, which is an exotic function object that wraps the original function object. Calling the bound function generally results in the execution of its wrapped function.
	*Example*

```js
	function log(level, time, message){
		console.log(level + time + message);
	}
	var logError = log.bind(null, 'today', 'error');
	logError('Server die!');
	->> Result: today error: Server die!
```

	- Call(): The call() method calls a functiion with a given this value and arguments provided individually
	*Example*

```js
	function greet(){
	  var reply = [this.person, 'Is An Awesome', this.role].join(' ');
	  console.log(reply);
	}
	var person = {person: 'Whis', role: 'student'};
	greet.call(person)
```

	-Apply(): The apply() method calls a function with a given this value, and arguments provided as an array

```js
	var a = [1, 5, 8, 9, 45];
	let min = Math.min.apply(null, a);
	console.log(min)
	let max = Math.max.apply(null, a)
	console.log(max)
```

**setTimeout and setInterval**

	- setTimeout: Executes a function, after waiting a specified number of milliseconds.
```js
	setTimeout(function, milliseconds);
```

	- clearTimeout: To stop setTimeout()
```js
	clearTimeout(myVar);
	with myVar = setTimeout(function, milliseconds);
```

	- setInterval: Same with setTimeout(), but repeats the execution of the function continously.
```js
	setInterval(function, milliseconds);
```

	-clearInterval: To stop setIntervl()
```js
	clearInterval(myVar);
	with myVar = setInterval(function, milliseconds);
```
**DOM - Document Object Model**

	- HTML DOM is a standard object model and programming interface for HTML:
		+ The HTML elements as objects
		+ The properties of all HTML elements
		+ The methods to access all HTML elements
		+ The events for all HTML elements
	- **DOM methods**
		+ DOM methods are actions you can perform.
		+ DOM properties are values that you can set or change.
	- **DOM Element**
		+ Finding HTML elements by: Tag Name/ Id/ Css/ Collection
	- **DOM CSS**
		+ Changing HTML Style ```document.getElementById(id).style.property = new style```
		+ Using Events: The HTML DOM allows you to execute code when an event occurs.