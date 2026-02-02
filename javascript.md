# JavaScript

+ [Files](#files)
+ [Functions](#functions)
    + [Async](#async)
+ [Modules](#modules)

## Files
External scripts usually have the file extension of `.js`. These files contain `JavaScript` code used across websites and applications. To include a `JavaScript` file in `HTML`, this can be placed before the closing `</body>` tag within a `<script>` tag. The `src` attribute is used to reference to path to the `JavaScript` file to be included.

```html
<script src="scripts/script.js"></script>

</body>
</html>
```

## Functions
A typical `JavaScript` function uses is defined using the `function` keyword.

```javascript
function testFunction() {
    // Code to be executed here
}

// Call the function to execute the code
testFunction()
```

This function can also be written using the `arrow` syntax.

```javascript
const testFunction = () => {
    // Code to be executed here
}

// Call the function to execute the code
testFunction()
```

### Async
The use of `async` is designed for anything that takes time: `timers`, `network requests`, or `files` are good examples of when to use `async`. 

A function runs from top to bottom. `JavaScript` waits for each line of code to finish before moving on. This is called `Synchronous (blocking)` execution. If `JavaScript` waits for everything to be executed, the application would be slow and potentially freeze. This is where `async (asynchronous)` comes in, which is non-blocking. Essentially: "Don't wait here, tell me when it's done."

+ Start a task
+ Moves on
+ Comes back later with the result

The modern approach in `JavaScript`:

+ `async` - marks a `function` as `asynchronous` and automatically returns a `promise`.
+ `await` - waits for a `promise` to finish (without blocking the app).

```javascript
function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Hello after 2 seconds"), 2000)
    })
}

async function testFunction() {
    console.log("Start")

    const message = await fetchData()

    console.log(message)
    console.log("End")
}

testFunction()
```

Output:

```shell
Start
(wait 2 seconds)
Hello after 2 seconds
End
```

## Modules
How a `function` is exported depends on the `module` system being used. A standard `function` works locally but needs to be a `module` to be exported and then imported elsewhere. A modern approach is to use `ES Modules (ESM)`. 

```javascript
export function testFunction() {
    // Code to be executed here
}
```

The function can then be `imported`:

```javascript
import { testFunction } from "./file.js"

// Call the function to execute the code
testFunction()
```

The `default` keyword can be applied and used like this:

```javascript
export default function testFunction() {
    // Code to be executed here
}
```

Import the function:

```javascript
import testFunction from "./file.js";
```

+ `React`, `Vite`, `Next.js` - use `ES Modules`
+ `Node 14+` with `"type": "module"` - use `ES Modules`
+ Older `Node` - uses `CommonJS`
