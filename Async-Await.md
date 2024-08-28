[Back to main](README.md#more-topic)

Below are more examples of how to use `async/await` in JavaScript. These examples cover a variety of scenarios, including error handling, parallel execution, sequential execution, and working with `async` functions in different contexts.

### **1. Basic `async/await` Example**
This is a simple example demonstrating how to use `async/await` to handle a Promise.
```javascript
async function fetchData() {
    return "Data fetched";
}

async function processData() {
    const data = await fetchData();
    console.log(data); // "Data fetched"
}

processData();
```

### **2. Error Handling with `try/catch`**
This example shows how to handle errors in an `async` function using `try/catch`.
```javascript
async function fetchData() {
    throw new Error("An error occurred while fetching data");
}

async function processData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error("Error:", error.message); // "Error: An error occurred while fetching data"
    }
}

processData();
```

### **3. Running Multiple `await` Calls in Sequence**
This example demonstrates running multiple `await` calls sequentially. Each `await` waits for the previous one to complete before continuing.
```javascript
async function fetchData1() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 1 fetched"), 1000));
}

async function fetchData2() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 2 fetched"), 2000));
}

async function fetchData3() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 3 fetched"), 1500));
}

async function processData() {
    const data1 = await fetchData1();
    console.log(data1); // "Data 1 fetched"

    const data2 = await fetchData2();
    console.log(data2); // "Data 2 fetched"

    const data3 = await fetchData3();
    console.log(data3); // "Data 3 fetched"
}

processData();
```

### **4. Running Multiple `await` Calls in Parallel with `Promise.all`**
This example shows how to run multiple asynchronous operations in parallel using `Promise.all`.
```javascript
async function fetchData1() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 1 fetched"), 1000));
}

async function fetchData2() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 2 fetched"), 2000));
}

async function fetchData3() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 3 fetched"), 1500));
}

async function processData() {
    const [data1, data2, data3] = await Promise.all([fetchData1(), fetchData2(), fetchData3()]);
    console.log(data1); // "Data 1 fetched"
    console.log(data2); // "Data 2 fetched"
    console.log(data3); // "Data 3 fetched"
}

processData();
```

### **5. `async/await` in a Loop**
This example demonstrates how to use `async/await` inside a loop to handle asynchronous operations.
```javascript
async function fetchData(num) {
    return new Promise((resolve) => setTimeout(() => resolve(`Data ${num} fetched`), 1000));
}

async function processAllData() {
    for (let i = 1; i <= 3; i++) {
        const data = await fetchData(i);
        console.log(data); // Logs "Data 1 fetched", then "Data 2 fetched", then "Data 3 fetched"
    }
}

processAllData();
```

### **6. Using `async/await` with `fetch` API**
This example shows how to use `async/await` to handle API requests using the `fetch` API.
```javascript
async function fetchData(url) {
    const response = await fetch(url);
    if (!response.ok) {
        throw new Error("Network response was not ok");
    }
    const data = await response.json();
    return data;
}

async function processData() {
    try {
        const data = await fetchData("https://jsonplaceholder.typicode.com/posts/1");
        console.log(data); // Logs the fetched post data
    } catch (error) {
        console.error("Fetch error:", error.message);
    }
}

processData();
```

### **7. Using `await` with Non-Promise Values**
This example demonstrates that `await` can be used with non-Promise values, and it will resolve them immediately.
```javascript
async function getValue() {
    return 42;
}

async function processValue() {
    const value = await getValue();
    console.log(value); // 42
}

processValue();
```

### **8. Using `await` with `Promise.resolve`**
This example shows how `await` works with `Promise.resolve` to immediately resolve a Promise.
```javascript
async function getResolvedValue() {
    return Promise.resolve("Resolved value");
}

async function processValue() {
    const value = await getResolvedValue();
    console.log(value); // "Resolved value"
}

processValue();
```

### **9. Using `await` with `Promise.reject`**
This example demonstrates how `await` handles a rejected Promise.
```javascript
async function getRejectedValue() {
    return Promise.reject("Rejected value");
}

async function processValue() {
    try {
        const value = await getRejectedValue();
        console.log(value);
    } catch (error) {
        console.error("Caught error:", error); // "Caught error: Rejected value"
    }
}

processValue();
```

### **10. Combining `async/await` with `Promise.allSettled`**
This example shows how to use `Promise.allSettled` with `async/await` to handle multiple Promises and get the status of each.
```javascript
async function fetchData1() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 1 fetched"), 1000));
}

async function fetchData2() {
    return new Promise((_, reject) => setTimeout(() => reject("Data 2 fetch failed"), 1500));
}

async function fetchData3() {
    return new Promise((resolve) => setTimeout(() => resolve("Data 3 fetched"), 2000));
}

async function processData() {
    const results = await Promise.allSettled([fetchData1(), fetchData2(), fetchData3()]);
    results.forEach((result) => {
        if (result.status === "fulfilled") {
            console.log("Success:", result.value);
        } else if (result.status === "rejected") {
            console.log("Failure:", result.reason);
        }
    });
}

processData();
```

### **11. Using `async/await` with `Array.map`**
This example demonstrates how to use `async/await` within an `Array.map` operation.
```javascript
async function fetchData(id) {
    return new Promise((resolve) => setTimeout(() => resolve(`Data for ID: ${id}`), 1000));
}

async function processIds(ids) {
    const promises = ids.map(async (id) => {
        const data = await fetchData(id);
        return data;
    });

    const results = await Promise.all(promises);
    console.log(results); // ["Data for ID: 1", "Data for ID: 2", "Data for ID: 3"]
}

processIds([1, 2, 3]);
```

### **12. Handling Timeouts with `async/await`**
This example demonstrates how to use `async/await` to handle timeouts in asynchronous operations.
```javascript
function timeout(ms) {
    return new Promise((_, reject) => {
        setTimeout(() => reject(new Error("Operation timed out")), ms);
    });
}

async function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => resolve("Data fetched successfully"), 3000);
    });
}

async function processData() {
    try {
        const data = await Promise.race([fetchData(), timeout(2000)]);
        console.log(data);
    } catch (error) {
        console.error("Error:", error.message); // "Error: Operation timed out"
    }
}

processData();
```

### **13. `async/await` in Event Listeners**
This example demonstrates how to use `async/await` within an event listener.
```javascript
document.getElementById("fetchButton").addEventListener("click", async function() {
    try {
        const data = await fetchData("https://jsonplaceholder.typicode.com/posts/1");
        console.log("Fetched data:", data);
    } catch (error) {
        console.error("Error fetching data:", error.message);
    }
});

async function fetchData(url) {
    const response = await fetch(url);
    const data = await response.json();
    return data;
}
```

### **14. Conditional `await` Execution**
This example shows how to conditionally execute `await` based on a certain condition.
```javascript
async function fetchData(shouldFetch) {
    if (shouldFetch) {
        const data = await new Promise((resolve) =>
            setTimeout(() => resolve("Data fetched"), 1000)
        );
        console.log(data);
    } else {
        console.log("Skipping data fetch");
    }
}

fetchData(true); // Waits and logs "Data fetched"
fetchData(false); // Immediately logs "Skipping data fetch"
```

### **15. Handling Multiple Dependencies with `async/await`**
This example

 demonstrates how to handle scenarios where the output of one async function depends on the output of another.
```javascript
async function fetchUser(userId) {
    return new Promise((resolve) =>
        setTimeout(() => resolve({ userId, username: "User" + userId }), 1000)
    );
}

async function fetchPosts(username) {
    return new Promise((resolve) =>
        setTimeout(() => resolve([`Post1 by ${username}`, `Post2 by ${username}`]), 1000)
    );
}

async function showUserPosts(userId) {
    const user = await fetchUser(userId);
    const posts = await fetchPosts(user.username);
    console.log("User:", user);
    console.log("Posts:", posts);
}

showUserPosts(1);
// Logs user details and posts after the operations are completed sequentially.
```
