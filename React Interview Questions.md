[Back to main](README.md#more-topic)

Here are the answers to the **JavaScript** and **React** related questions from the image:

---

### **JavaScript:**

1. **Explain major differences between the ES5 and ES6 syntax with relevant examples.**
   - **Block scoping**: ES6 introduced `let` and `const` to replace `var` for block-scoped variables.
     ```javascript
     // ES5
     var x = 10;

     // ES6
     let y = 20;
     const z = 30;
     ```
   - **Arrow functions**: ES6 introduced arrow functions that have a simpler syntax and do not bind their own `this`.
     ```javascript
     // ES5
     function sum(a, b) {
       return a + b;
     }

     // ES6
     const sum = (a, b) => a + b;
     ```
   - **Template literals**: In ES6, you can use backticks for string interpolation.
     ```javascript
     // ES5
     var message = 'Hello ' + name;

     // ES6
     const message = `Hello ${name}`;
     ```

2. **Axios vs Fetch and are there other options?**
   - **Axios**:
     - Automatically transforms JSON data.
     - Supports older browsers.
     - Better error handling.
   - **Fetch**:
     - Built into the browser.
     - Requires manual handling of JSON transformation (`response.json()`).
   - Other options: `Superagent`, `jQuery.ajax`.

3. **ES6 Concepts**
   - Some key ES6 features include:
     - `let` and `const`
     - Arrow functions
     - Template literals
     - Default function parameters
     - Destructuring assignment
     - Modules (import/export)

4. **What is event loop?**
   - The **event loop** is a mechanism in JavaScript that allows non-blocking I/O operations. It continuously checks if the call stack is empty and processes the callback queue (for events, promises, etc.) when the stack is clear.

5. **Spread operator and rest operator?**
   - **Spread Operator (`...`)**: Expands elements of an array or object into individual elements.
     ```javascript
     const arr = [1, 2, 3];
     const newArr = [...arr, 4, 5];
     ```
   - **Rest Operator (`...`)**: Collects multiple elements into an array.
     ```javascript
     function sum(...numbers) {
       return numbers.reduce((acc, num) => acc + num, 0);
     }
     ```

6. **Arrow function**
   - Arrow functions provide a concise syntax and do not bind their own `this` context.
   ```javascript
   const greet = name => `Hello, ${name}`;
   ```

7. **What is a promise?**
   - A **promise** is an object that represents the eventual completion (or failure) of an asynchronous operation.
   ```javascript
   const fetchData = new Promise((resolve, reject) => {
     setTimeout(() => resolve('Data received'), 1000);
   });
   ```

8. **What is closure?**
   - A **closure** is a function that has access to its outer function’s variables, even after the outer function has returned.
   ```javascript
   function outer() {
     let count = 0;
     return function inner() {
       count++;
       console.log(count);
     };
   }
   const counter = outer();
   counter(); // 1
   counter(); // 2
   ```

9. **Explain use of Babel**
   - **Babel** is a JavaScript compiler that converts ES6+ code into backward-compatible JavaScript to support older browsers or environments.

10. **Object and array destructuring**
   - **Destructuring** allows extracting values from objects or arrays easily.
   ```javascript
   // Array destructuring
   const [a, b] = [1, 2];

   // Object destructuring
   const { name, age } = { name: 'John', age: 30 };
   ```

11. **Differences between `var`, `let`, and `const` and why var should not be used**
   - `var`: Function-scoped, can be re-declared, hoisted.
   - `let`: Block-scoped, cannot be re-declared, not hoisted.
   - `const`: Block-scoped, cannot be re-assigned or re-declared.
   - **Avoid `var`** because it can cause unexpected behavior due to hoisting and lack of block scope.

12. **Explain hoisting in JavaScript with use case**
   - **Hoisting** is JavaScript’s behavior of moving declarations to the top of the current scope.
   ```javascript
   console.log(x); // undefined
   var x = 5;
   ```

13. **Difference between async and sync**
   - **Synchronous**: Code is executed line by line. Each operation waits for the previous one to finish.
   - **Asynchronous**: Code can run without waiting for previous operations to complete (e.g., promises, callbacks).

---

### **React:**

1. **What is virtual DOM?**
   - The **virtual DOM** is a lightweight, in-memory representation of the actual DOM. React uses it to efficiently update the real DOM by only changing elements that have actually changed.

2. **Explain React component Life Cycle**
   - The React component lifecycle includes:
     - **Mounting**: `constructor()`, `render()`, `componentDidMount()`
     - **Updating**: `shouldComponentUpdate()`, `render()`, `componentDidUpdate()`
     - **Unmounting**: `componentWillUnmount()`

3. **How do you pass data to parent in React component?**
   - You can pass data to a parent component using a callback function passed as a prop.
   ```javascript
   function Parent() {
     const handleData = (data) => console.log(data);
     return <Child sendData={handleData} />;
   }

   function Child({ sendData }) {
     return <button onClick={() => sendData('Data from Child')}>Send</button>;
   }
   ```

4. **Difference between functional and class component, tell me the use case?**
   - **Functional components**: Simple and stateless (though hooks can add state and lifecycle methods).
   - **Class components**: Can have state and lifecycle methods.
   - **Use case**: Functional components are preferred for simpler, stateless components, while class components may be used for more complex state management (although hooks are reducing this distinction).

5. **Why should we not update the state directly?**
   - Directly modifying the state won’t trigger a re-render and may cause unpredictable behavior. Always use `setState()` in class components or the `useState()` hook in functional components.

6. **What is the difference between HTML and React event handling?**
   - React event handlers are named using camelCase (`onClick` instead of `onclick`) and are passed as functions, whereas HTML event handlers are strings.

7. **Difference between Shadow DOM and Virtual DOM?**
   - **Virtual DOM**: React’s concept of optimizing DOM updates.
   - **Shadow DOM**: A browser technology used to encapsulate a component's styles and markup (used in Web Components).

8. **What are uncontrolled components? - Examples**
   - **Uncontrolled components** use the native DOM to manage form inputs, with values accessed via `refs` instead of state.
   ```javascript
   const inputRef = useRef(null);
   const handleSubmit = () => {
     console.log(inputRef.current.value);
   };
   return <input ref={inputRef} />;
   ```

9. **How to write comments in React?**
   - JSX comments are written inside curly braces.
   ```jsx
   {/* This is a comment */}
   ```

---


### 1. **What are uncontrolled components? - Examples**
   **Uncontrolled components** are form elements in React where the form data is handled by the DOM itself instead of React. You use `ref` to access the value of the form elements.

   **Example:**
   ```jsx
   function UncontrolledForm() {
     const inputRef = React.useRef(null);

     const handleSubmit = (e) => {
       e.preventDefault();
       console.log(inputRef.current.value);
     };

     return (
       <form onSubmit={handleSubmit}>
         <input type="text" ref={inputRef} />
         <button type="submit">Submit</button>
       </form>
     );
   }
   ```

### 2. **How to write comments in React?**
   In JSX, you can write comments by wrapping them inside curly braces within the JSX.
   ```jsx
   {/* This is a comment in JSX */}
   ```

### 3. **Stateful and stateless components**
   - **Stateful components** (also called "Class Components" or components that use the `useState` hook) hold and manage their internal state.
     ```jsx
     class StatefulComponent extends React.Component {
       state = { count: 0 };
       render() {
         return <div>{this.state.count}</div>;
       }
     }
     ```
   - **Stateless components** (also called "Functional Components") don't have an internal state.
     ```jsx
     const StatelessComponent = () => <div>Hello World</div>;
     ```

### 4. **Is it good to use `setState()` in `componentWillMount()` method?**
   No, it's not recommended to use `setState()` in `componentWillMount()`. This method is deprecated, and using `setState()` in it causes unnecessary renders. It’s better to use `componentDidMount()` or, in functional components, `useEffect()`.

### 5. **What are the possible return types of `render()` method?**
   The `render()` method in React can return:
   - JSX (which compiles to a `React.Element`)
   - `null` (for rendering nothing)
   - `false` (to avoid rendering anything)
   - Arrays (for returning multiple elements)
   - Fragments (i.e., `<React.Fragment></React.Fragment>` or `<> </>`)

### 6. **What are React Server components?**
   **React Server Components** allow rendering React components on the server and sending the UI updates to the client. This feature is aimed at optimizing the rendering of apps by avoiding unnecessary client-side JavaScript.

### 7. **Can you loop inside JSX?**
   Yes, you can loop inside JSX using methods like `map()`. 

   **Example:**
   ```jsx
   const items = ['apple', 'banana', 'orange'];
   const itemList = items.map(item => <li key={item}>{item}</li>);
   return <ul>{itemList}</ul>;
   ```

### 8. **Explain the three dots (Spread operator) in React**
   The **spread operator** (`...`) is used to pass all properties of an object, combine objects/arrays, or copy them.

   **Example:**
   ```jsx
   const obj1 = { a: 1, b: 2 };
   const obj2 = { ...obj1, c: 3 }; // { a: 1, b: 2, c: 3 }
   ```

### 9. **How do you force a React component to re-render without calling its state method?**
   You can use `this.forceUpdate()` in class components to force a re-render. In functional components, you can change the state or props to trigger a re-render.

### 10. **How to update an object with `setState()`?**
   You should use the **spread operator** to update an object’s properties when using `setState()`.

   **Example:**
   ```jsx
   this.setState(prevState => ({
     user: { ...prevState.user, name: 'John' }
   }));
   ```

### 11. **Why do we use `render()` in React?**
   The `render()` method in React is used to tell React what to display on the screen. It returns the UI as JSX, which React then renders to the DOM.

### 12. **Explain various lifecycle methods of React components**
   In class components, React lifecycle methods include:
   - **componentDidMount**: Invoked after the component is mounted. Used for side effects like data fetching.
   - **componentDidUpdate**: Invoked after the component updates. Used for responding to state/prop changes.
   - **componentWillUnmount**: Called right before the component is removed from the DOM. Used for cleanup.
   - **getDerivedStateFromProps**: Invoked before rendering when new props or state are received.
   - **shouldComponentUpdate**: Decides whether the component should re-render.

### 13. **How does React quickly update the HTML DOM, and how does it find the exact element to update?**
   React uses a **virtual DOM**. When the state of a component changes, React creates a virtual representation of the DOM and compares it to the previous version. This process is called **reconciliation**. React then updates only the parts of the DOM that changed (known as **DOM diffing**).

### 14. **What are the distinct features of React?**
   - **Component-Based Architecture**: Reusable, encapsulated components.
   - **Virtual DOM**: Efficient rendering by minimizing direct DOM manipulations.
   - **Unidirectional Data Flow**: Data flows from parent to child, making debugging easier.
   - **JSX**: A syntax extension that allows writing HTML-like code in JavaScript.
   - **Hooks**: Allowing functional components to use state and other React features.
   - **Declarative UI**: Describes the UI based on the current state, making code predictable.



Here are the answers to the questions related to **Hooks**, **Refs**, and **React Context API** from the image:

### **Hooks:**

1. **What is `useMemo` hook? Give a use case scenario, project wise.**
   - `useMemo` is a React hook used for memoizing expensive calculations to avoid unnecessary re-renders.
   - **Use Case**: In a dashboard application, if you have a large dataset and want to filter it based on certain criteria, you can use `useMemo` to memoize the filtered results so that they are recalculated only when the dependencies change (e.g., filter criteria).
   ```jsx
   const filteredData = useMemo(() => {
     return data.filter(item => item.value > threshold);
   }, [data, threshold]);
   ```

2. **How to fetch data with React Hooks?**
   - You can fetch data using `useEffect` and `useState` hooks.
   ```jsx
   function FetchData() {
     const [data, setData] = useState(null);
     useEffect(() => {
       fetch('https://api.example.com/data')
         .then(response => response.json())
         .then(data => setData(data));
     }, []);
     
     return <div>{data ? JSON.stringify(data) : 'Loading...'}</div>;
   }
   ```

3. **Write the code, bring the button on the page (event), package details, basic hooks sample program**
   ```jsx
   function ButtonComponent() {
     const [count, setCount] = useState(0);

     const handleClick = () => setCount(count + 1);

     return (
       <div>
         <button onClick={handleClick}>Click me</button>
         <p>You clicked {count} times</p>
       </div>
     );
   }
   ```

4. **How to stop `useEffect` from executing?**
   - You can stop `useEffect` from executing by returning a cleanup function or by controlling the dependencies array. If you want `useEffect` to run only once, pass an empty dependency array.
   ```jsx
   useEffect(() => {
     return () => {
       // Cleanup code here to stop execution
     };
   }, []);
   ```

5. **Component unmount and `useEffect`**
   - When a component unmounts, React calls the cleanup function inside `useEffect`. This is useful for clearing resources like timers, event listeners, or subscriptions.
   ```jsx
   useEffect(() => {
     const timer = setInterval(() => console.log('Running...'), 1000);
     return () => clearInterval(timer); // Cleanup on unmount
   }, []);
   ```

6. **Use case of hooks in terms of dealing with data**
   - Hooks like `useState` and `useEffect` help manage state and perform side effects in functional components. For example, you can use them to fetch and store data from an API, handle form inputs, or manage dynamic content.

7. **What are the hooks you have used till date?**
   - Common hooks: `useState`, `useEffect`, `useMemo`, `useCallback`, `useContext`, `useReducer`, `useRef`, `useLayoutEffect`, `useImperativeHandle`, `useDebugValue`.

8. **How `componentDidMount` work in `useEffect`?**
   - In React functional components, the equivalent of `componentDidMount` is using `useEffect` with an empty dependency array. This makes the effect run only once after the initial render.
   ```jsx
   useEffect(() => {
     console.log('Component mounted');
   }, []);
   ```

9. **In `useEffect`, what happens when a dependency is not declared?**
   - If you don't declare a dependency in `useEffect`, the effect will not re-run when that dependency changes. This can lead to stale closures or unexpected behaviors.

10. **In `useEffect`, how `addEventListener` and `removeEventListener` work? Explain with example.**
   - You can add event listeners inside `useEffect` and remove them in the cleanup function to avoid memory leaks.
   ```jsx
   useEffect(() => {
     const handleResize = () => console.log('Window resized');
     window.addEventListener('resize', handleResize);

     return () => {
       window.removeEventListener('resize', handleResize); // Cleanup
     };
   }, []);
   ```

---

### **Refs:**

1. **What is the use of refs?**
   - Refs are used to access DOM elements directly or to store mutable values that persist across renders without causing re-renders.
   ```jsx
   const inputRef = useRef(null);
   const focusInput = () => inputRef.current.focus();
   ```

2. **What are forward refs?**
   - **Forward refs** allow passing refs from parent to child components to access DOM nodes or other refs in the child component.
   ```jsx
   const ChildComponent = React.forwardRef((props, ref) => (
     <input ref={ref} />
   ));

   function ParentComponent() {
     const inputRef = useRef(null);
     return <ChildComponent ref={inputRef} />;
   }
   ```

---

### **React Context API:**

1. **Use case for using Context API in React**
   - The Context API is used for passing data (like user authentication, theme, or settings) through the component tree without having to pass props manually at every level.
   ```jsx
   const ThemeContext = React.createContext();

   function App() {
     const theme = 'dark';
     return (
       <ThemeContext.Provider value={theme}>
         <Toolbar />
       </ThemeContext.Provider>
     );
   }

   function Toolbar() {
     return <ThemedButton />;
   }

   function ThemedButton() {
     const theme = useContext(ThemeContext);
     return <button className={theme}>Button</button>;
   }
   ```

2. **Explain Context API**
   - The **Context API** allows you to create global variables or state that can be shared among components. You define a context and provide it to components, enabling access to values without having to pass props down the entire tree.

   **Steps:**
   1. Create a context using `React.createContext()`.
   2. Use `Context.Provider` to pass the value down the component tree.
   3. Access the context value using `useContext(Context)` in functional components or `Context.Consumer` in class components.



Here are the answers to the **Redux** and **React Performance Optimization** related questions from the image:

### **Redux:**

1. **Redux Observables**
   - **Redux Observable** is a middleware that uses **RxJS** to handle asynchronous actions in Redux. It allows handling side effects in Redux by using streams and operators from RxJS.
   - Example: Dispatching async actions or managing complex event streams.
   ```javascript
   import { ofType } from 'redux-observable';
   import { mapTo } from 'rxjs/operators';

   const pingEpic = action$ => action$.pipe(
     ofType('PING'),
     mapTo({ type: 'PONG' })
   );
   ```

2. **How to reset state in Redux?**
   - To reset Redux state, you can handle a specific action (e.g., `RESET_STATE`) in your root reducer, which sets the state back to its initial value.
   ```javascript
   const rootReducer = (state, action) => {
     if (action.type === 'RESET_STATE') {
       return initialState;
     }
     return appReducer(state, action);
   };
   ```

3. **How to make AJAX request in Redux?**
   - You can make AJAX requests using middlewares like **Redux Thunk** or **Redux Saga**. With **Redux Thunk**, you can dispatch asynchronous actions like this:
   ```javascript
   export const fetchData = () => async dispatch => {
     const response = await fetch('https://api.example.com/data');
     const data = await response.json();
     dispatch({ type: 'FETCH_DATA_SUCCESS', payload: data });
   };
   ```

4. **Purpose of the constants in Redux?**
   - Constants are used to define action types in Redux. They help avoid typos and make it easier to manage actions across a large codebase.
   ```javascript
   export const FETCH_DATA = 'FETCH_DATA';
   ```

5. **What is redux-saga?**
   - **Redux-Saga** is a middleware for handling side effects in Redux by using generator functions. It allows handling complex async operations like AJAX calls, timeouts, or event listening in a more manageable way.
   ```javascript
   function* fetchDataSaga() {
     const response = yield call(fetch, 'https://api.example.com/data');
     const data = yield response.json();
     yield put({ type: 'FETCH_DATA_SUCCESS', payload: data });
   }
   ```

6. **How to set initial state in Redux?**
   - You can set the initial state by passing it as the second argument to the reducer function.
   ```javascript
   const initialState = { count: 0 };

   function counterReducer(state = initialState, action) {
     switch (action.type) {
       case 'INCREMENT':
         return { count: state.count + 1 };
       default:
         return state;
     }
   }
   ```

7. **Can you dispatch Redux with a timeout? If yes, explain.**
   - Yes, using middlewares like **Redux Thunk** or **Redux Saga**, you can dispatch actions with a timeout.
   - **Example with Thunk:**
   ```javascript
   export const dispatchWithTimeout = () => dispatch => {
     setTimeout(() => {
       dispatch({ type: 'TIMEOUT_ACTION' });
     }, 1000);
   };
   ```

8. **How will you distinguish Redux from Flux?**
   - **Redux**:
     - Single store for the whole application.
     - Reducers are pure functions.
     - Predictable state management.
   - **Flux**:
     - Multiple stores.
     - More complex and less predictable.

9. **Define Reducers in React?**
   - Reducers are pure functions that take the current state and an action as arguments and return a new state based on the action.
   ```javascript
   function reducer(state, action) {
     switch (action.type) {
       case 'INCREMENT':
         return { count: state.count + 1 };
       default:
         return state;
     }
   }
   ```

10. **What is a store in Redux?**
    - The store is the object that holds the entire state tree of the application. It allows dispatching actions and subscribing to state changes.
    ```javascript
    const store = createStore(reducer);
    ```

11. **Function of reducer**
    - The reducer function determines how the state should change in response to an action. It takes the current state and action and returns the updated state.

12. **Can we use multiple stores?**
    - It is recommended to use a **single store** in Redux. If you need to manage multiple pieces of state, you should combine reducers using `combineReducers()`.
    ```javascript
    const rootReducer = combineReducers({ user: userReducer, posts: postReducer });
    ```

13. **How to handle Redux async functionality - Redux Observables**
    - With Redux Observables, you can handle async actions using RxJS streams. You use `epics` to observe and handle action streams.
    ```javascript
    const fetchEpic = action$ =>
      action$.pipe(
        ofType('FETCH_DATA'),
        mergeMap(() => ajax.getJSON('/api/data')
          .pipe(map(response => ({ type: 'FETCH_DATA_SUCCESS', payload: response }))))
      );
    ```

---

### **React Performance Optimization:**

1. **How to optimize the performance?**
   - **Memoization**: Use `React.memo`, `useMemo`, and `useCallback` to prevent unnecessary re-renders.
   - **Code Splitting**: Use dynamic imports and `React.lazy()` to load components only when needed.
   - **Virtualize large lists**: Use libraries like **react-window** to render only the visible portion of large lists.
   - **Avoid anonymous functions in JSX**: Avoid creating new function references on every render.
   - **Optimize images**: Use proper image formats, lazy loading, and compression.

2. **What is React lazy function?**
   - `React.lazy()` allows loading components lazily via code splitting. It helps improve performance by loading components only when needed.
   ```javascript
   const LazyComponent = React.lazy(() => import('./LazyComponent'));

   function App() {
     return (
       <Suspense fallback={<div>Loading...</div>}>
         <LazyComponent />
       </Suspense>
     );
   }
   ```

3. **What is React memo?**
   - `React.memo` is a higher-order component (HOC) that memoizes functional components. It prevents re-renders if the props have not changed, improving performance.
   ```javascript
   const MyComponent = React.memo(function MyComponent({ name }) {
     return <div>{name}</div>;
   });
   ```



### **React Events:**

1. **Define Synthetic Events in React?**
   - **Synthetic events** are React's cross-browser wrapper around the browser's native events. React's event system is a lightweight wrapper that provides a consistent API across different browsers. It works similarly to native browser events but provides additional performance improvements and compatibility.
   ```jsx
   function handleClick(event) {
     console.log(event.type); // 'click'
   }

   return <button onClick={handleClick}>Click Me</button>;
   ```

---

### **Error Boundaries:**

1. **Error boundaries in React v16**
   - **Error Boundaries** are React components that catch JavaScript errors anywhere in their child component tree, log the error, and display a fallback UI instead of crashing the entire application.
   - They were introduced in React v16 and can be used by defining either `componentDidCatch` or `getDerivedStateFromError` lifecycle methods.
   ```jsx
   class ErrorBoundary extends React.Component {
     constructor(props) {
       super(props);
       this.state = { hasError: false };
     }

     static getDerivedStateFromError(error) {
       return { hasError: true };
     }

     componentDidCatch(error, errorInfo) {
       console.log(error, errorInfo);
     }

     render() {
       if (this.state.hasError) {
         return <h1>Something went wrong.</h1>;
       }

       return this.props.children;
     }
   }
   ```

2. **In which scenarios error boundaries do not catch errors?**
   - Error boundaries **do not catch** the following types of errors:
     - Errors inside **event handlers** (you must use `try/catch` in event handlers).
     - Asynchronous errors (like those in `setTimeout` or `requestAnimationFrame`).
     - Errors thrown in the **server-side rendering (SSR)** process.
     - Errors thrown during the execution of the **error boundary itself**.

3. **Difference between try-catch block and error boundaries?**
   - **Error Boundaries**:
     - Designed specifically to handle errors in React component trees.
     - They can catch errors in rendering, lifecycle methods, and constructors of the whole tree.
     - React will automatically switch to the fallback UI when an error is caught by the error boundary.
   - **Try-catch**:
     - Can catch errors anywhere, but not during rendering or lifecycle methods in React.
     - Useful for synchronous code like event handlers, promises, or async functions.

---

### **React Router:**

1. **Best way to navigate React Router**
   - The best way to navigate in React Router is by using the `useNavigate()` hook (in React Router v6) or `history.push()` (in React Router v5).
   - **React Router v6 Example:**
   ```jsx
   import { useNavigate } from 'react-router-dom';

   function MyComponent() {
     const navigate = useNavigate();

     return <button onClick={() => navigate('/home')}>Go Home</button>;
   }
   ```

2. **How to get query params with React Router?**
   - In React Router v6, you can get query parameters using the `useSearchParams` hook.
   ```jsx
   import { useSearchParams } from 'react-router-dom';

   function MyComponent() {
     const [searchParams] = useSearchParams();
     const name = searchParams.get('name');

     return <div>Name: {name}</div>;
   }
   ```

3. **How does the React Router differ from conventional routing?**
   - **Conventional Routing**:
     - Typically involves loading a new HTML page for every route change, requiring a full-page reload.
   - **React Router**:
     - Implements **client-side routing**, which allows for changing the view without reloading the page.
     - Uses a virtual DOM to manage the UI based on the route.
     - It is declarative: You define routes as components, and React Router renders the correct UI based on the URL.
     - Supports nested routes, dynamic routing, and route guards.

---


