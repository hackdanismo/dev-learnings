# React
`React` is an open-source front-end JavaScript library, created by `Meta` (formally Facebook), to build user interfaces based on reusable components. 

+ [Install](#install)
+ [Run Server](#run-server)

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
