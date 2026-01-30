# JavaScript

+ [Files](#files)
+ [Functions](#functions)

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
