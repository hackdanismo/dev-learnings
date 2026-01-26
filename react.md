# React
`React` is an open-source front-end JavaScript library, created by `Meta` (formally Facebook), to build user interfaces based on reusable components. 

+ [Install](#install)
+ [Run Server](#run-server)
+ [Setup](#setup)
+ [Components](#components)
    + [Building a Component](#building-a-component)
    + [Import a Component](#import-a-component)
    + [Props](#props)
        + [Default Prop Values](#default-prop-values)
+ [Styling](#styling)
    + [CSS Modules](#css-modules)
    + [Inline Styles](#inline-styles)
    + [CSS-in-JS](#css-in-js)

## Install
`Vite` can be used to setup and scaffold a `React` application. This can replace - the now legacy - `create-react-app` tool that was used previously. 

Ensure that the version of `Node` installed is a version that is compatible with `Vite`. This setup is in reference to `Vite v7.3.1` so could change in future.

Run the following terminal command and follow the prompts in the CLI. This will allow a`TypeScript` or `JavaScript` `React` application to be generated. `Vite` can also be used to setup applications using frameworks or libraries such as `Vue`, `Angular` and `Svelte`:

```shell
$ npm create vite@latest

# Yarn
$ yarn create vite
# pnpm
$ pnpm create vite
# Bun
$ bun create vite
# Deno
$ deno init --npm vite
```
<img width="578" height="281" alt="Screenshot of the terminal showing the frameworks and libraries supported by Vite." src="https://github.com/user-attachments/assets/1a7ed7fc-eaec-4433-b36c-be60c3582af6" />

When making a section from the list in the CLI once `React` is selected, the language is being chosen (`JavaScript` or `TypeScript`), the `compiler/transpiler` picked and sometimes a `routing` or `framework layer` is also to be included. 

<img width="578" height="330" alt="Screenshot of the terminal showing the list of options when React has been selected." src="https://github.com/user-attachments/assets/1693d952-07e8-46c0-8801-10eb4c9cbdc2" />

Once the setup has been completed the application will be running on the default port on `localhost`: [http://localhost:5173/](http://localhost:5173/) and the application can be viewed inside a browser.

<img width="1622" height="859" alt="The React application running on localhost." src="https://github.com/user-attachments/assets/7ea8d412-1547-40b0-8f6d-e5a6d9c1642c" />

The file structure in the `src` directory of the app that has been generated will look something like this:

```
src/
├─ assets/
│  └─ react.svg
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

To stop the development server and stop the application from within the terminal, use the keyboard command: `control` + `c`.

## Run Server
To run the `development server` to view the application locally on `localhost`, use the terminal command:

```shell
$ npm run dev
```

## Setup
The initial `React` setup using `Vite` has a file named `App.tsx`. This is a component. The code can be simplified to render `Hello, World` on the page by updating this file. The CSS stylesheet has also be removed to avoid any default styling from being applied.

```typescript
// src/App.tsx

function App() {
    return (
        <>
            <h1>Hello, World</h1>
        </>
    )
}

export default App
```

A component can be written using `arrow syntax` for the function instead of the typical `function` keyword, if required.

```typescript
// src/App.tsx

const App = () => {
    return (
        <>
            <h1>Hello, World</h1>
        </>
    )
}

export default App
```

In the `main.tsx` file, also remove the line that imports the `index.css` stylesheet to have no styling applied to the application.

```typescript
import './index.css'
```

The `main.tsx` file will now look like this:

```typescript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'

import App from './App.tsx'

createRoot(document.getElementById('root')!).render(
    <StrictMode>
        <App />
    </StrictMode>,
)
```

<img width="1622" height="470" alt="The application running in the browser with no CSS styles applied." src="https://github.com/user-attachments/assets/390fb3d4-e84a-4c86-871a-9af28e885f03" />

## Components
`React` applications are usually made up of reusable blocks, known as `Components`. It is often recommended to add the components to a folder in the project `src` directory named `components` to make them easier to find. The file structure would look something like this:

```
src/
├─ assets/
│  └─ react.svg
│
├─ components/
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

Within the `components` sub-directory a folder can be added for each component - for example, a `Button` - and an `index.tsx` file can be added containing the code for the component itself. `TypeScript` uses `.tsx` files whilst `JavaScript` uses `.jsx` files. In this application, `TypeScript` is being used.

```
src/
├─ assets/
│  └─ react.svg
│
├─ components/
│  └─ Button/
│      └─ index.tsx
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

A simple `Hello` component written in `TypeScript` to render `Hello` followed by a name, would have the following code within a file named `index.tsx`. This would be inside of the `components` folder and then inside of a sub-directory named `Hello`:

```typescript
// src/components/Hello/index.tsx

type HelloProps = {
    name: string;
};

const Hello = ({ name }: HelloProps) => {
    return <h1>Hello, {name}</h1>;
};

export default Hello;
```
This `TypeScript` example uses the `arrow function` syntax.

The file structure:

```
src/
├─ assets/
│  └─ react.svg
│
├─ components/
│  └─ Hello/
│      └─ index.tsx
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

### Building a Component
A simple `component` in `React`, without any `props`, could look like this `Button` example:

```typescript
// src/components/Button/index.tsx

const Button = () => {
    return <button>Button</button>;
};

export default Button;
```

The semicolons can be removed as both `JavaScript` and `TypeScript` have `Automatic Semicolon Insertion (ASI)`. The component can be updated without having semicolons.

```typescript
// src/components/Button/index.tsx

const Button = () => {
    return <button>Button</button>
}

export default Button
```

The `export` keyword is used to allow the component to be imported into another component or page across the application.

Once a component is created it can be imported into other components and pages within the `React` application. This allows a component to be truly resuable.

### Import a Component
Once a component has been created it can then be imported into another component or page within the `React` application. The `import` keyword is used to import a component followed by the name of the component and the location/file path. 

```typescript
import Button from './components/Button'
```

To import the `Button` component into the `App.tsx` file, the code would look like this (code comments have been added for clarity):

```typescript
// src/App.tsx

// Use the import keyword to import the component into this component
import Button from './components/Button'

function App() {
    return (
        <>
            {/* Render the Button component here */}
            <Button />
        </>
    )
}

export default App
```

The component then needs to be rendered within the component from within the function. This is added by using a `tag-like` syntax (e.g. `<Button />`). This is self-closing initially. The `Button` component will now render on the page or within the component.

```typescript
<Button />
```

It is simple to reuse this component in other components and on pages, as this example shows with the `Button` component being rendered three times:

```typescript
// src/App.tsx

// Use the import keyword to import the component into this component
import Button from './components/Button'

function App() {
    return (
        <>
            {/* Render the Button component here multiple times */}
            <Button />
            <Button />
            <Button />
        </>
    )
}

export default App
```

The use of the `<>` and `</>` fragments wrapped around multiple components, avoids errors occuring and avoids the use of an empty `<div>` element that would then be rendered in the `DOM (Document Object Model)`. A fragement is not needed if a single component is being returned, only needed for multiple components.

```typescript
{/* The fragment is wrapped around multiple components, not needed for a single component */}
<>
    <Button />
    <Button />
    <Button />
</>
```

### Props
To pass data to a component, `props` - known as `properties` - can be used. 

To begin, in `TypeScript`, the `prop types` need to be defined. For the `children` prop, this will be set to: `React.ReactNode` (as an example). This is set within an object named `type`. This applies `type checking` to all props that are used to check the data type that is being passed and ensure that it is valid. This helps to avoid potential bugs and issues.


```typescript
type TyoeProps = {
    prop: React.ReactNode
}
```

Once the `prop types` are defined, this needs to be set within the `function`:

```typescript
const Component = ({ prop }: TypeProps) => {
    return <tag>{prop}</tag>
}
```

In the `Button` component example, a `children` `prop` can be used. This is a core `React` idea. The `children` prop is a special prop that represents whatever is placed between the opening and closing tags. This is ideal for the label of a `Button`. Here is the updated `Button` component:

```typescript
type ButtonProps = {
    children: React.ReactNode
}

const Button = ({ children }: ButtonProps) => {
    return <button>{children}</button>
}

export default Button
```

When the `Button` component is being rendered, this now needs to have a label placed between an opening and closing tag. The `prop` allows the `Button` component to be reused and each button to have its own label. In this example, the label is set to be `Settings`.

```typescript
{/* Without a children prop, a self-closing tag */}
<Button />

{/* With a children prop, using and opening and closing tag with the label text between */}
<Button>Settings</Button>
```

#### Default Prop Values
To avoid empty `props`, a `default value` can be assigned to a prop. This ensures that if no value is passed to the component, the default value will be rendered and this can avoid any potential issues or errors.

```typescript
type ButtonProps = {
    children?: React.ReactNode
}

const Button = ({ children = "Button" }: ButtonProps) => {
    return <button>{children}</button>
}

export default Button
```

To understand this further there are two main changes. The first, adding a `?` at the end of the `children` prop type checking, turns the prop to be optional:

```typescript
type ButtonProps = {
    // The '?' added turns the prop to be optional and not required
    children?: React.ReactNode
}
```

The second change is the addition of the string `"Button"` as the default value itself. This ensures that if no value is passed into the `children` prop, this default value will be used instead.

```typescript
// Use the default value of "Button" for the label if no value is passed into the component
const Button = ({ children = "Button" }: ButtonProps) => {
    return <button>{children}</button>
}
```

So when using the component with `default prop values`:

```typescript
{/* This will render the default value of "Button" as its label */}
<Button />

{/* This will render the value passed to the component of "Settings" as its label */}
<Button>Settings</Button>
```

## Styling
Once a `React` application has been created and components added, styling can be applied. The simplest approach is to create a `CSS` stylesheet and import it into the individual component. Here is how the file structure would look using the `Button` component as an example:

```
src/
├─ assets/
│  └─ react.svg
│
├─ components/
│  └─ Button/
│      └─ index.tsx
│      └─ styles.css
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

The `CSS` stylesheet can then be imported and used within the component:

```typescript
import "./styles.css"

type ButtonProps = {
    children?: React.ReactNode
}

const Button = ({ children = "Button" }: ButtonProps) => {
    return <button className="btn">{children}</button>
}

export default Button
```

In `React`, the `className` attribute is used to apply classes to a component as `class` is a reserved keyword and cannot be used. The styling can also be written in either `.css` or `.scss` files.

### CSS Modules
Unlike the standard use of `CSS stylesheets` to apply styling which adds styling to the global scope, `CSS Modules` allows styling to be locally scoped to the component itself. This still uses standard `CSS` syntax.

```
src/
├─ assets/
│  └─ react.svg
│
├─ components/
│  └─ Button/
│      └─ index.tsx
│      └─ Button.module.css
│
├─ App.css
├─ App.tsx
├─ index.css
├─ main.tsx
```

The `CSS Module` file would look like this:

```css
/* Button.module.css */
.button {
    background: blue;
}
```

This is then imported using the `import` keyword inside of the component:

```typescript
import styles from "./Button.module.css"

type ButtonProps = {
    children?: React.ReactNode
}

const Button = ({ children = "Button" }: ButtonProps) => {
    return <button className={styles.button}>{children}</button>
}

export default Button
```

### Inline Styles
The `style` attribute can be used to apply styling without the use of an external stylesheet, however, media queries and psuedo classes cannot be used.

```typescript
type ButtonProps = {
    children?: React.ReactNode
}

const Button = ({ children = "Button" }: ButtonProps) => {
    return <button style={{ backgroundColor: "blue", padding: 12 }}>>{children}</button>
}

export default Button
```

### CSS in JS
Using `CSS-in-JS` allows styles to be generated at runtime. The styles are scoped to the components and dynamic styling can be applied using `props`. The syntax can be more complicated and there are more overheads/abstraction to consider but this is great for use in design systems and component libraries. A package such as `Styled Components` can be used for `React` and `React Native` projects to apply `CSS-in-JS`.

To use the `Styled Components` package:

```shell
$ npm install styled-components
# Also, install this if using TypeScript:
$ npm install -D @types/styled-components
```

Update the component to use the `styled-components` package:

```typescript
import styled from "styled-components"

type ButtonProps = {
  children?: React.ReactNode
}

// Styled button definition
const StyledButton = styled.button`
    background-color: #2563eb;
    color: white;
    padding: 0.5rem 1rem;
    border-radius: 0.375rem;
    border: none;
    font-size: 1rem;
    cursor: pointer;

    &:hover {
        background-color: #1e40af;
    }

    &:active {
        transform: translateY(1px);
    }

    &:disabled {
        opacity: 0.6;
        cursor: not-allowed;
    }
`;

// Your component stays simple
const Button = ({ children = "Button" }: ButtonProps) => {
    return <StyledButton>{children}</StyledButton>;
}

export default Button
```
