
## Hoàng Văn Tùng - 08/04

### Day 3 + 4

**This, Call, Apply, Bind**

*The this Method*
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

*The Bind() method*

The bind() method creates a new function where “this” refers to the parameter in the parenthesis in the above case “car”. This way the bind() method enables calling a function with a specified “this” value.

```js
var car = { 
    registrationNumber: "29F1",
    brand: "Honda",

    displayDetails: function(ownerName){
        console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
    }
}
```

*Call And Apply Method* 

- Similar but slightly different usage provide the call() and apply() methods which also belong to the Function.prototype property.
- When using the apply() function the parameter must be placed in an array. Call() accepts both an array of parameters and a parameter itself. Both are great tools for borrowing functions in JavaScript.
- Bind(), call() and apply() functions can make your life easier when you need to set the value of ‘this’

```js
var car = { 
    registrationNumber: "29F1",
    brand: "Honda"
}

function displayDetails(ownerName) {
    console.log(ownerName + ", this is your car: " + this.registrationNumber + " " + this.brand);
}
```

**SetTimeout/ClearTimeout**
- clearTimeout()
  - The clearTimeout() function in javascript clears the timeout which has been set by setTimeout()function before that.

- setTimeout() function takes two parameters. First a function to be executed and second after how much time (in ms).
- setTimeout() executes the passed function after given time. The number id value returned by setTimeout() function is stored in a variable and it’s passed into the clearTimeout() function to clear the timer.

var t;
  
        function color() {
            if (document.getElementById('btn').style.color == 'blue') {
                document.getElementById('btn').style.color = 'green';
            } else {
                document.getElementById('btn').style.color = 'blue';
            }
  
        }
  
        function fun() {
            t = setTimeout(color, 3000);
  
        }
  
        function stop() {
            clearTimeout(t);
        }

**SetInterval/ClearInterval**

- ClearInterval()
   - The clearInterval() function in javascript clears the interval which has been set by setInterval() function before that.

- SetInterval() function takes two parameters. First a function to be executed and second after how much time (in ms).
- SetInterval() executes the passed function for the given time interval. The number id value returned by setInterval() function is stored in a variable and it’s passed into the clearInterval() function to clear the interval.

```js
var t;
  
        function color() {
            if (document.getElementById('btn').style.color == 'blue') {
                document.getElementById('btn').style.color = 'green';
            } else {
                document.getElementById('btn').style.color = 'blue';
            }
  
        }
  
        function fun() {
            t = setInterval(color, 3000);
  
        }
  
        function stop() {
            clearInterval(t);
        }
```