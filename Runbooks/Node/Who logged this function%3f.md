```js
let callerName;
try {
	throw new Error();
} catch ({ stack }) {
	const regex = /(\w+)@|at (\w+) \(/g;
	// You need to call exec twice
	regex.exec(stack);
	const captures = regex.exec(stack);
	callerName = captures[1] || captures[2];
}
console.log(callerName);
```



>[!info]- Example
>```js
const helloWorld = () => noOp()
helloWorld() // logs: helloWorld
> ```