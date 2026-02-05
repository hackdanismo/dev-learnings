# JavaScript

+ [Files](#files)
+ [Functions](#functions)
    + [Async](#async)
+ [Modules](#modules)
+ [Map](#map)

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
`Modules` are files that have their own private scope and can explicitly share code with other files using `import` and `export`. Think of them as self-contained pieces of code that can be connected together.

How a `function` is exported depends on the `module` system being used. A standard `function` works locally but needs to be a `module` to be exported and then imported elsewhere. A modern approach is to use `ES Modules (ESM)`. `ESM` lets JavaScript files share code safely using `import` and `export`. Before `ESM`, `JavaScript` had no built-in module system. `ESM` fixed this by adding `modules` to the language spec itself.

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

In `HTML` a `JavaScript` script can be loaded as an `ES Module (ESM)` rather than a traditional script.

```html
<script type="module" src="dist/index.js"></script>
```

The `type="module"` part of the `<script>` is the important part here. This changes how the browser treats the file and enables `ES Module` behavior. This allows the browser to support: `import`, `export`, `separate module scope` and `dependency loading`. So when we use imports, like the example below, these only work inside of modules:

```javascript
import { mountAll } from "./core/mount";
import "./components/counter";
```

The error of: `Uncaught SyntaxError: Cannot use import statement outside a module` would be thrown if a normal `JavaScript` script was included in the `HTML`. This method automatically defers the script, so no `defer` attribute is required. 

```html
<script type="module" src="dist/index.js"></script>
<!-- Behaves like: -->
<script defer src="dist/index.js"></script>
```

`Modules` in `JavaScript` are also always in `strict mode` by default.

## Map
A `JavaScript` `Map` is a built-in object for storing `key` / `value` pairs. Think of it like a `dictionary` or `hash table`. It answers the question: `"Given this key, what value is stored?"`. A simple example:

```javascript
const ages = new Map();

ages.set("Alice", 25);
ages.set("Bob", 30);

ages.get("Alice"); // 25
ages.has("Bob");   // true
```

A `Map` in `TypeScript` looks exactly like JavaScript's Map, but `types` are added so `TypeScript` can check your `keys` and `values`.

```typescript
const map = new Map<KeyType, ValueType>();
```

A simple example:

```typescript
const ages = new Map<string, number>();

ages.set("Alice", 25);
ages.set("Bob", 30);
```
