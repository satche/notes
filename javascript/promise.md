# [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

Promise is an object which return the result (succsess or failure) of an [asynchronous operation](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Introducing). It handles two [callbacks](https://developer.mozilla.org/en-US/docs/Glossary/Callback_function) precised in the arguments of a function: one in case of success (resolve), the other in case of failure (reject).

The result is handle by the `then()` method, which takes two argument: one for the success (the promise is resolved), and a facultative one for the error (the promise is rejected).

```javascript
const promise = new Promise((resolve, reject) => {
	if (Math.random() >= 0.5) {
		resolve("Success");
	} else {
		reject("Error (less than 0.5)");
	}
});

promise.then(
	success => console.log(success), // "Success"
	error => console.log(error) // "Error (less than 0.5)"
);
```

## [async function](https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Statements/async_function)

Enable asynchronous for the function. Let handle promises in a cleaner way.

```javascript
let asyncCall = async () => {
	let result = await promise();
	console.log(result);
}

handlePromise(); // log result of the promise
```
