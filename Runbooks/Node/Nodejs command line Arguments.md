The property `process.argv` is an array of all arguments passed including command being executed.

```js
console.log(process.argv)
```

Executed will output

```bash
$ node . test1 test2
[
  '/home/metru/.nvm/versions/node/v14.15.4/bin/node',
  '/home/metru/dev/repo/projectRoot',
  'test1',
	'test2'
]
```

Easy way to parse this is using `slice`

```js
const args = process.argv.slice(2)
// Alternatively
const [arg1, arg2, arg3, ...rest] = process.argv.slice(2)
```