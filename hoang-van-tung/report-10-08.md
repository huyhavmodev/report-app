## Hoàng Văn Tùng - 08/10

### Week 2 (Continue)

**AJAX and JSON**

- Ajax(Asynchronous Javascript and XML): Ajax exhanges data and update parts of web page without reloading the whole web. It uses XmlHttpRequest objects to communicate with web server by Js.

![alt text](https://images.viblo.asia/d0276277-2c0d-45e1-96d4-a1c652070871.png)

- Json(Javascript Object Notation): Json is lightweight format for storing and transporting data. Json is often used hen data is sent from a server to a web page.

```Js
	{
	"employees":[
	    {"firstName":"John", "lastName":"Doe"},
	    {"firstName":"Anna", "lastName":"Smith"},
	    {"firstName":"Peter", "lastName":"Jones"}
	]
	}
```

**Async/Await, promise**

- Promise is a Javascript object that links producing code and consuming code. Promises are a mechanism in JavaScript that helps you perform asynchronous tasks without falling into callback hell.

```Js
	let myPromise = new Promise((resolve, reject) => {
		resole(); //when successful
		reject(); //when raise error
	});

	promise.then(
		function(value){...},
		function(error){...}
	);
```

- Async/Await: the keyword async before a function makes the function return a promise. To hepl solve asynchronous proplem more efficiel

```Js
	async function myProject(){
		let value = await promise;
	}
```

**Ajax request**

- The XMLHttpRequest object is used to exchange data with a server.
	+ To send a request to a server, we use the open() and send() methods to the XMLHttpRequest object:
```js
	xhttp.open("GET", "ajax_infor.txt", true);
	xhttp.send();
```

| Method | Description |
|--------|-------------|
|open(method, url, async)|Specifies the type of request<br>method: GET or POST<br>url: the server location <br>aysnc: true or false|
|send()  | Sends the request to the server (used for GET)|
|send(string)| Sends the request to the server(used for POST)|   

- Fetch API: is a simple API for sending and receiving request by Javascript. With fetch, it is easier to make and handle the respond easier than old XMLHttpRequest.

**ES6**

- Arrow function:

```js
	(args) => {...};
```

- Scope: 

```js
	var i; // i is function scope
	let x; // x and y is block scope
	const y;
```

- default parameter: 

```js
	function myFunc(a = 1, b = 2){
		c = a + b;
		console.log(c);
	}

	myFunc(); // => result is 3 because when I call function, i don't parse value so function will take default value
```

- Rest:

```js
	function mySum(...args){
	var sum = 0;
	args.forEach((i)=>{
	 sum += i;
	})
	return sum;
	}

	console.log(mySum(1,2,9,7));	
```