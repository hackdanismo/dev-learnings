# JavaScript

+ [Files](#files)
+ [Functions](#functions)
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
