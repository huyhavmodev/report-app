# Day 3 + 4 (continue)

**Cookie/localStorage/sessionStorage**

- Cookie: Is a small piece of data stored on the user's computer by the web browser while browsing a website. Cookies were designed to be a reliable mechanism for website to remember stateful information or record the user's browsing activity. Authentication cookies are the most common method used by web servers to know whether the user is logged in or not, and which account they are logged in with.
	+ Different types of cookies: Magic cookies and HTTP cookies
	+ With a few variations, cookies in the cyber world come in two types: session and persistent cookies.
		+ Session cookies are used only while navigating a website. They are stored in random access memory and ae nerver written to the hard drive.
		+ Peristent cookies remain on a computer indefinitely, although many include an expiration date and are automatically removed when that date is reached.

- localStorage and sessionStorage properties allow to save key/value pairs in a web browser.
	+ The localStage objects store data with no expiration date. And The localStorage property is read only.
- Browser Object Model: allows Js communicate with the browser.
	+ Js Window: The window object is supported by all browsers. It represents the browser's window. Some methods: Size, Object, open, close, moveTo, resizeTo.
	+ Js Screen: the window.Screen object contais information about the user's screen. Some properties: width, height, availWidth, availHeight, colorDepth, pixelDepth.
	+ Js location: the location object can be used to geet the current page address and to redirect the browser to a new page. Some properties: href, hostname, pathname, protocol, assign.
	+ Js history: the history object contains the browser history. Some properties: back, forward.
	+ Js navigator: The navigator object contains information about the visitor's browser. Some examples: appName, appCodeName, platform.
	+ Js Popup Boxes: These are three kind of popup boxes: Alert box, confirm box and Prompt box.
	+ Js Timing: The timing object allows execution of code at specified time interval. The two key method to use with Js are: 
	```js
		setTimeout() and setInterval.
	```

** Callback **
	- Callback helps us develop asynchronous Js code and keeps us safe from problems and errors.
	It makes sure that a function is not going to run before a task is completed bt will run right after the task has completed.
	- A callback is a function passed as an argument to another function.
```js
	function hW(){
		alert("Hello World");
	}
	function firstTask(callback){
		callback();
	}
	hW(firstTask);
```
	- Callback hell: callback hell in javascript is just that you make too many nested callbacks.
```js
	getData(function(a){  
	    getMoreData(a, function(b){
	        getMoreData(b, function(c){ 
	            getMoreData(c, function(d){ 
	                getMoreData(d, function(e){ 
	                    ...
	                });
	            });
	        });
	    });
	});		
```