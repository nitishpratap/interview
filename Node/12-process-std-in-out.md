# process.argv

**Introduction to `process.argv`:**
`process.argv` is a property in Node.js that provides access to the command-line arguments passed to the Node.js process. When you run a Node.js script from the command line, you can pass additional arguments, and these arguments can be accessed through the `process.argv` array.

**Usage:**
The `process.argv` array is an array of strings, where the first two elements are reserved for system-specific information:

- `process.argv[0]`: The absolute path to the Node.js executable.
- `process.argv[1]`: The absolute path to the JavaScript file being executed.

The command-line arguments start from index 2 onwards (`process.argv[2]` and beyond), where `process.argv[2]` is the first user-provided argument.

**Example:**
Suppose you run the following Node.js script from the command line:

```javascript
// myScript.js

console.log(process.argv);
```

If you execute the script with the following command:

```bash
node myScript.js arg1 arg2 arg3
```

The output will be an array containing the command-line arguments:

```
[
  '/path/to/node',     // process.argv[0]
  '/path/to/myScript.js', // process.argv[1]
  'arg1',              // process.argv[2]
  'arg2',              // process.argv[3]
  'arg3'               // process.argv[4]
]
```

**Process stdout - Standard Output:**
`process.stdout` is a writable stream provided by Node.js that represents the standard output (stdout) of the current process. It allows you to write data to the console or terminal.

**Usage:**
You can use `process.stdout.write()` to write data to the console. The data is displayed in the console immediately without adding a newline at the end.

**Example:**
```javascript
process.stdout.write('Hello, ');
process.stdout.write('Node.js!');
```

Output:
```
Hello, Node.js!
```

**Process stdin - Standard Input:**
`process.stdin` is a readable stream provided by Node.js that represents the standard input (stdin) of the current process. It allows you to read data from the console or terminal.

**Usage:**
You can use `process.stdin` to listen for user input from the console. By default, `process.stdin` is in paused mode, so you need to explicitly resume it and handle the 'data' and 'end' events to read the input.

**Example:**
```javascript
process.stdin.resume();

process.stdin.on('data', (data) => {
  const input = data.toString().trim();
  console.log(`You entered: ${input}`);
});

process.stdin.on('end', () => {
  console.log('No more data.');
});
```

When you run this script and enter data in the console, the 'data' event will be triggered, and the input will be displayed:

```
$ node myScript.js
Type something and press Enter:
Hello, Node.js! // You enter this text
You entered: Hello, Node.js!
No more data.   // Press Ctrl + D (Linux/Mac) or Ctrl + Z (Windows) to end input
```

**Summary:**
- `process.argv` is an array that provides access to the command-line arguments passed to the Node.js process.
- `process.stdout` is a writable stream representing the standard output of the current process and is used to write data to the console.
- `process.stdin` is a readable stream representing the standard input of the current process and is used to read data from the console.

Using `process.argv`, `process.stdout`, and `process.stdin`, you can interact with the command line, read user input, and display output from your Node.js applications. These features are particularly useful when building command-line tools or interactive applications that require user interaction.
