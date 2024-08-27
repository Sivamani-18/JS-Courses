Here are some additional examples of Promises to give you a deeper understanding of how they work in JavaScript.

### **1. Basic Promise Example**
This example demonstrates how to create a basic Promise that resolves or rejects based on a condition.
```javascript
function checkNumber(num) {
    return new Promise(function(resolve, reject) {
        if (num > 10) {
            resolve("The number is greater than 10");
        } else {
            reject("The number is 10 or less");
        }
    });
}

checkNumber(15)
    .then(function(message) {
        console.log(message); // "The number is greater than 10"
    })
    .catch(function(error) {
        console.log(error); // Not executed
    });

checkNumber(8)
    .then(function(message) {
        console.log(message); // Not executed
    })
    .catch(function(error) {
        console.log(error); // "The number is 10 or less"
    });
```

### **2. Chaining Promises**
This example shows how you can chain multiple Promises together using `.then()` to perform a series of asynchronous operations in sequence.
```javascript
function fetchData() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Data fetched");
        }, 1000);
    });
}

function processData(data) {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve(data + " and processed");
        }, 1000);
    });
}

function saveData(data) {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve(data + " and saved");
        }, 1000);
    });
}

fetchData()
    .then(function(data) {
        console.log(data); // "Data fetched"
        return processData(data);
    })
    .then(function(data) {
        console.log(data); // "Data fetched and processed"
        return saveData(data);
    })
    .then(function(data) {
        console.log(data); // "Data fetched and processed and saved"
    })
    .catch(function(error) {
        console.log("Error:", error);
    });
```

### **3. Handling Multiple Promises with `Promise.all`**
This example demonstrates how to execute multiple Promises concurrently and wait for all of them to resolve using `Promise.all`.
```javascript
function fetchUser() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("User data fetched");
        }, 1000);
    });
}

function fetchPosts() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Posts data fetched");
        }, 2000);
    });
}

function fetchComments() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Comments data fetched");
        }, 1500);
    });
}

Promise.all([fetchUser(), fetchPosts(), fetchComments()])
    .then(function(results) {
        console.log(results); // ["User data fetched", "Posts data fetched", "Comments data fetched"]
    })
    .catch(function(error) {
        console.log("Error:", error);
    });
```

### **4. Handling the First Resolved Promise with `Promise.race`**
`Promise.race` returns the result of the first resolved or rejected promise.
```javascript
function fastPromise() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Fast promise resolved");
        }, 500);
    });
}

function slowPromise() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Slow promise resolved");
        }, 2000);
    });
}

Promise.race([fastPromise(), slowPromise()])
    .then(function(result) {
        console.log(result); // "Fast promise resolved"
    })
    .catch(function(error) {
        console.log("Error:", error);
    });
```

### **5. Using `Promise.allSettled`**
`Promise.allSettled` waits for all the promises to either resolve or reject and returns an array of objects representing the outcome of each promise.
```javascript
function fetchData(success) {
    return new Promise(function(resolve, reject) {
        setTimeout(function() {
            if (success) {
                resolve("Data fetched successfully");
            } else {
                reject("Data fetch failed");
            }
        }, 1000);
    });
}

Promise.allSettled([fetchData(true), fetchData(false), fetchData(true)])
    .then(function(results) {
        results.forEach(function(result) {
            if (result.status === "fulfilled") {
                console.log("Success:", result.value);
            } else if (result.status === "rejected") {
                console.log("Failure:", result.reason);
            }
        });
    });
```

### **6. Sequential Promises with `Array.reduce`**
This example shows how to execute a series of asynchronous operations sequentially using an array of Promises and `Array.reduce`.
```javascript
function createPromise(data, delay) {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve(data);
        }, delay);
    });
}

const tasks = [
    () => createPromise("First task", 1000),
    () => createPromise("Second task", 2000),
    () => createPromise("Third task", 1500),
];

tasks.reduce(function(promiseChain, currentTask) {
    return promiseChain.then(function(chainResults) {
        return currentTask().then(function(currentResult) {
            return [...chainResults, currentResult];
        });
    });
}, Promise.resolve([])).then(function(results) {
    console.log("All tasks completed:", results);
    // Output after 4.5 seconds: ["First task", "Second task", "Third task"]
});
```

### **7. Retrying a Promise on Failure**
This example demonstrates how to retry a Promise operation a specific number of times if it fails.
```javascript
function fetchWithRetry(url, retries) {
    return new Promise(function(resolve, reject) {
        function attemptFetch(attempt) {
            fetch(url)
                .then(resolve)
                .catch(function(error) {
                    if (attempt < retries) {
                        console.log("Retrying... Attempt:", attempt + 1);
                        attemptFetch(attempt + 1);
                    } else {
                        reject(error);
                    }
                });
        }
        attemptFetch(0);
    });
}

fetchWithRetry("https://jsonplaceholder.typicode.com/posts/1", 3)
    .then(function(response) {
        return response.json();
    })
    .then(function(data) {
        console.log("Data fetched:", data);
    })
    .catch(function(error) {
        console.log("Fetch failed after 3 retries:", error);
    });
```

### **8. Creating a Custom Promise-based Timeout**
This example creates a custom `timeout` function that returns a Promise, which resolves after a specified duration.
```javascript
function timeout(ms) {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Timeout completed after " + ms + "ms");
        }, ms);
    });
}

timeout(2000).then(function(message) {
    console.log(message); // "Timeout completed after 2000ms"
});
```
