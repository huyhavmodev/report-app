
## Hoàng Văn Tùng - 08/05

### Day 3 + 4 (Continue)


**Cookie/localStorage/sessionStorage**

*Cookie*
A Cookie can be set from a HTTP header. Usually the server that you're trying to reach, if it has cookies, will send an HTTP header like this: 
```js
    Set-Cookie: choco_chip_cookie=its_delicious
```

- To see the Cookies you have, if you have Firefox, from your devtools, go to storage -> Cookies; if you have Chrome, from your devtools, go to Application -> storage -> Cookies. Most websites use Cookies, you should find some there 

*localStorage/sessionStorage*

- Unlike Cookies where all Cookies (for that domain) are sent on each request, Local and Session Storage data aren't sent on each HTTP request. They just sit in your browser until someone requests it. 

```js
    sessionStorage.setItem('strawberry', 'pancake');
    sessionStorage.getItems('strawberry'); // pancake`

    sessionStorage.chocolate = 'waffle';
    sessionStorage.chocolate; // waffle

    sessionStorage['blueberry'] = 'donut';
    sessionStorage['blueberry']; // donut;

    delete sessionStorage.strawberry;
```

- The main difference between Local and Session storage is that Local Storage has no expiration date while Session Storage data are gone when you close the browser tab - hence the name "session".

```js
    localStorage.setItem('strawberry', 'pancake');
    localStorage.getItems('strawberry'); // pancake`

    localStorage.chocolate = 'waffle';
    localStorage.chocolate; // waffle

    localStorage['blueberry'] = 'donut';
    localStorage['blueberry']; // donut;

    delete localStorage.strawberry;
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


**Callback**

- A callback function is a function that is passed as an argument to another function, to be “called back” at a later time. A function that accepts other functions as arguments is called a higher-order function, which contains the logic for when the callback function gets executed. It’s the combination of these two that allow us to extend our functionality.

```js
function createQuote(quote, callback){ 
  var myQuote = "Like I always say, " + quote;
  callback(myQuote); // 2
}

function logQuote(quote){
  console.log(quote);
}

createQuote("eat your vegetables!", logQuote); // 1

// Result in console: 
// Like I always say, eat your vegetables!
```

- 