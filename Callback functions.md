[Back to main](README.md#more-topic)

Here are several examples of how to use callback functions in JavaScript. A callback function is a function that is passed into another function as an argument and is executed after some operation has been completed.

### **1. Basic Callback Function Example**

Here’s a simple example of a callback function:

```javascript
function greeting(name) {
    console.log('Hello ' + name);
}

function processUserInput(callback) {
    const name = prompt('Please enter your name.');
    callback(name);
}

processUserInput(greeting);
```

#### **Explanation:**

- **greeting:** A function that takes a `name` and logs a greeting message.
- **processUserInput:** A function that prompts the user for their name and then calls the provided callback function (`greeting` in this case) with the entered name.
- **processUserInput(greeting):** Here, `greeting` is passed as a callback function, so when `processUserInput` runs, it eventually calls `greeting(name)`.

### **2. Asynchronous Callback Example**

Callbacks are often used for asynchronous operations such as fetching data from an API:

```javascript
function fetchData(callback) {
    setTimeout(() => {
        const data = { id: 1, name: 'John Doe' };
        callback(data);
    }, 2000); // Simulating a network request with a 2-second delay
}

function displayData(data) {
    console.log('Received data:', data);
}

fetchData(displayData);
```

#### **Explanation:**

- **fetchData:** Simulates fetching data with a `setTimeout` to mimic a delayed operation (like a network request). After 2 seconds, it calls the `callback` with the data.
- **displayData:** A function that logs the received data to the console.
- **fetchData(displayData):** `displayData` is passed as a callback to `fetchData`, which calls it after fetching the data.

### **3. Callback with Array Methods**

Array methods like `map`, `filter`, and `forEach` use callback functions.

```javascript
const numbers = [1, 2, 3, 4, 5];

const doubled = numbers.map(function(number) {
    return number * 2;
});

console.log(doubled); // [2, 4, 6, 8, 10]
```

#### **Explanation:**

- **numbers.map:** Takes a callback function that is applied to each element of the array. The callback here multiplies each number by 2.
- **doubled:** The result is a new array with all the numbers doubled.

### **4. Custom Callback Example**

You can create your own functions that accept callbacks for more complex operations.

```javascript
function doMath(a, b, callback) {
    return callback(a, b);
}

const add = function(x, y) {
    return x + y;
};

const subtract = function(x, y) {
    return x - y;
};

console.log(doMath(5, 3, add)); // 8
console.log(doMath(5, 3, subtract)); // 2
```

#### **Explanation:**

- **doMath:** A function that takes two numbers and a callback function. It returns the result of the callback function when passed the numbers `a` and `b`.
- **add and subtract:** Two callback functions that perform addition and subtraction.
- **doMath(5, 3, add):** Calls `doMath` with `5` and `3`, and the `add` callback, returning the sum (8).
- **doMath(5, 3, subtract):** Calls `doMath` with `5` and `3`, and the `subtract` callback, returning the difference (2).

### **5. Callback with Error Handling**

It’s common to see callbacks used in a pattern that allows error handling, especially in asynchronous operations.

```javascript
function fetchData(callback) {
    setTimeout(() => {
        const error = false; // Change to true to simulate an error
        if (error) {
            callback('Error: Unable to fetch data', null);
        } else {
            const data = { id: 1, name: 'John Doe' };
            callback(null, data);
        }
    }, 2000);
}

function handleResponse(error, data) {
    if (error) {
        console.log(error);
    } else {
        console.log('Received data:', data);
    }
}

fetchData(handleResponse);
```

#### **Explanation:**

- **fetchData:** This function simulates an asynchronous operation (like fetching data from an API). It calls the callback with either an error or data.
- **handleResponse:** A callback function that checks if there's an error. If there is, it logs the error; otherwise, it processes the data.
- **fetchData(handleResponse):** Executes `fetchData`, which eventually calls `handleResponse` with either an error or the data.

### **6. Chaining Callbacks**

Sometimes you may need to execute multiple callbacks in sequence:

```javascript
function firstTask(callback) {
    console.log('First Task');
    callback();
}

function secondTask(callback) {
    console.log('Second Task');
    callback();
}

function thirdTask() {
    console.log('Third Task');
}

firstTask(function() {
    secondTask(thirdTask);
});
```

#### **Explanation:**

- **firstTask:** Logs "First Task" and then calls the `callback`.
- **secondTask:** Logs "Second Task" and then calls the `callback`.
- **thirdTask:** Logs "Third Task".
- **Chaining:** The `firstTask` is executed first. Once it's done, it calls the `secondTask`, which then calls the `thirdTask`.

### **Summary**

Callbacks are an essential part of JavaScript, especially for handling asynchronous operations like fetching data, file operations, or event handling. Understanding how to use callbacks effectively will help you write more flexible and powerful JavaScript code.
