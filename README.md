# JavaScript Object Methods, Array Methods, and Advanced JavaScript Examples

This repository provides examples of common JavaScript object methods, array methods, and advanced JavaScript concepts. The focus is primarily on ES5 features, with some ES6 methods included for completeness.

 
[Online Compiler](https://www.programiz.com/javascript/online-compiler/)

## Table of Contents
- [Object Methods](#object-methods)
  - [Object.keys()](#objectkeys)
  - [Object.values()](#objectvalues)
  - [Object.entries()](#objectentries)
  - [Object.assign()](#objectassign)
  - [Object.create()](#objectcreate)
  - [Object.freeze()](#objectfreeze)
  - [Object.seal()](#objectseal)
  - [Object.getOwnPropertyNames()](#objectgetownpropertynames)
  - [Object.defineProperty()](#objectdefineproperty)
  - [Object.defineProperties()](#objectdefineproperties)
  - [Object.getPrototypeOf()](#objectgetprototypeof)
  - [Object.is()](#objectis)
  - [Object.isExtensible()](#objectisextensible)
  - [Object.preventExtensions()](#objectpreventextensions)
  - [Object.hasOwnProperty()](#objecthasownproperty)
  - [Object.propertyIsEnumerable()](#objectpropertyisenumerable)
  - [Object.toString()](#objecttostring)
  - [Object.valueOf()](#objectvalueof)
- [Array Methods](#array-methods)
  - [push()](#push)
  - [pop()](#pop)
  - [shift()](#shift)
  - [unshift()](#unshift)
  - [slice()](#slice)
  - [splice()](#splice)
  - [concat()](#concat)
  - [join()](#join)
  - [reverse()](#reverse)
  - [sort()](#sort)
  - [indexOf()](#indexof)
  - [lastIndexOf()](#lastindexof)
  - [forEach()](#foreach)
  - [map()](#map)
  - [filter()](#filter)
  - [reduce()](#reduce)
  - [reduceRight()](#reduceright)
  - [some()](#some)
  - [every()](#every)
  - [find()](#find)
  - [findIndex()](#findindex)
  - [isArray()](#isarray)
  - [toString()](#tostring)
  - [valueOf()](#valueof)
- [Loops, Objects, and Arrays](#loops-objects-and-arrays)
  - [Looping Through an Array](#looping-through-an-array)
  - [Looping Through an Object](#looping-through-an-object)
  - [Nested Loops](#nested-loops)
  - [Object Creation and Access](#object-creation-and-access)
  - [Array Manipulation](#array-manipulation)
- [Advanced JavaScript Examples](#advanced-javascript-examples)
  - [Higher-Order Functions](#higher-order-functions)
  - [Currying](#currying)
  - [Debouncing](#debouncing)
  - [Throttling](#throttling)
  - [Event Delegation](#event-delegation)
  - [Promise Chaining](#promise-chaining)
  - [Dynamic Imports](#dynamic-imports)
  - [Generators](#generators)
  - [Proxy Object](#proxy-object)
  - [Closures with Private Variables](#closures-with-private-variables)
  - [Custom Error Handling](#custom-error-handling)
  - [Async Iterators](#async-iterators)
  - [Memoization](#memoization)
  - [Template Literals](#template-literals)
  - [Destructuring Assignment](#destructuring-assignment)
  - [Promises](#promises)
  - [Async/Await](#asyncawait)
  - [Shallow Copy and Deep Copy](#shallow-copy-and-deep-copy)

## Object Methods

### Object.keys()
Returns an array of a given object's own enumerable property names.
```javascript
var person = {
    name: "John",
    age: 30,
    city: "New York"
};

var keys = Object.keys(person);
console.log(keys); // ["name", "age", "city"]
```

### Object.values()
Returns an array of a given object's own enumerable property values.
```javascript
var person = {
    name: "John",
    age: 30,
    city: "New York"
};

var values = Object.values(person);
console.log(values); // ["John", 30, "New York"]
```

### Object.entries()
Returns an array of a given object's own enumerable property [key, value] pairs.
```javascript
var person = {
    name: "John",
    age: 30,
    city: "New York"
};

var entries = Object.entries(person);
console.log(entries); // [["name", "John"], ["age", 30], ["city", "New York"]]
```

### Object.assign()
Copies all enumerable own properties from one or more source objects to a target object. It returns the target object.
```javascript
var target = { a: 1 };
var source = { b: 2, c: 3 };

var returnedTarget = Object.assign(target, source);
console.log(returnedTarget); // { a: 1, b: 2, c: 3 }
```

### Object.create()
Creates a new object with the specified prototype object and properties.
```javascript
var person = {
    fullName: function() {
        return this.firstName + " " + this.lastName;
    }
};

var john = Object.create(person);
john.firstName = "John";
john.lastName = "Doe";
console.log(john.fullName()); // "John Doe"
```

### Object.freeze()
Freezes an object, preventing new properties from being added and existing properties from being modified or deleted.
```javascript
var obj = {
    prop: 42
};

Object.freeze(obj);

obj.prop = 33; // No effect, as the object is frozen
console.log(obj.prop); // 42
```

### Object.seal()
Seals an object, preventing new properties from being added and marking all existing properties as non-configurable.
```javascript
var obj = {
    prop: 42
};

Object.seal(obj);

obj.prop = 33; // Works, as the property is writable
console.log(obj.prop); // 33

delete obj.prop; // Fails silently or throws in strict mode
console.log(obj.prop); // 33
```

### Object.getOwnPropertyNames()
Returns an array of all properties (including non-enumerable properties) found directly in a given object.
```javascript
var obj = {
    name: "John",
    age: 30
};

var props = Object.getOwnPropertyNames(obj);
console.log(props); // ["name", "age"]
```

### Object.defineProperty()
Defines a new property directly on an object, or modifies an existing property on an object, and returns the object.
```javascript
var obj = {};

Object.defineProperty(obj, "name", {
    value: "John",
    writable: false,
    enumerable: true,
    configurable: false
});

console.log(obj.name); // "John"

obj.name = "Doe"; // Cannot change the value as writable is false
console.log(obj.name); // "John"
```

### Object.defineProperties()
Defines new or modifies existing properties directly on an object, returning the object.
```javascript
var obj = {};

Object.defineProperties(obj, {
    name: {
        value: "John",
        writable: true
    },
    age: {
        value: 30,
        writable: false
    }
});

console.log(obj.name); // "John"
console.log(obj.age); // 30
```

### Object.getPrototypeOf()
Returns the prototype (i.e., the value of the internal `[[Prototype]]` property) of the specified object.
```javascript
var person = {
    name: "John",
    age: 30
};

var proto = Object.getPrototypeOf(person);
console.log(proto); // {} (The prototype of plain objects is Object.prototype)
```

### Object.is()
Compares if two values are the same value. It is similar to the `===` operator but differs in handling special cases.
```javascript
console.log(Object.is(25, 25)); // true
console.log(Object.is(NaN, NaN)); // true
console.log(Object.is(0, -0)); // false
```

### Object.isExtensible()
Determines if an object is extensible (i.e., whether new properties can be added to it).
```javascript
var obj = {};
console.log(Object.isExtensible(obj)); // true

Object.preventExtensions(obj);
console.log(Object.isExtensible(obj)); // false
```

### Object.preventExtensions()
Prevents new properties from ever being added to an object (i.e., prevents future extensions to the object).
```javascript
var obj = { name: "John" };

Object.preventExtensions(obj);
obj.age = 30; // Fails silently or throws in strict mode

console.log(obj.age); // undefined
```

### Object.hasOwnProperty()
Returns a boolean indicating whether the object has the specified property as its own property (as opposed to inheriting it).
```javascript
var person = {
    name: "John"
};



console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("age")); // false
```

### Object.propertyIsEnumerable()
Returns a boolean indicating whether the specified property is enumerable.
```javascript
var person = {
    name: "John"
};

console.log(person.propertyIsEnumerable("name")); // true

Object.defineProperty(person, "age", {
    value: 30,
    enumerable: false
});

console.log(person.propertyIsEnumerable("age")); // false
```

### Object.toString()
Returns a string representing the object.
```javascript
var obj = { name: "John", age: 30 };
console.log(obj.toString()); // "[object Object]"
```

### Object.valueOf()
Returns the primitive value of the specified object.
```javascript
var obj = { name: "John" };
console.log(obj.valueOf()); // { name: "John" }
```

## Array Methods

### push()
Adds one or more elements to the end of an array and returns the new length of the array.
```javascript
var fruits = ["Apple", "Banana"];
fruits.push("Orange");
console.log(fruits); // ["Apple", "Banana", "Orange"]
```

### pop()
Removes the last element from an array and returns that element.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
var last = fruits.pop();
console.log(last); // "Orange"
console.log(fruits); // ["Apple", "Banana"]
```

### shift()
Removes the first element from an array and returns that element. This method changes the length of the array.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
var first = fruits.shift();
console.log(first); // "Apple"
console.log(fruits); // ["Banana", "Orange"]
```

### unshift()
Adds one or more elements to the beginning of an array and returns the new length of the array.
```javascript
var fruits = ["Banana", "Orange"];
fruits.unshift("Apple");
console.log(fruits); // ["Apple", "Banana", "Orange"]
```

### slice()
Returns a shallow copy of a portion of an array into a new array object. The original array is not modified.
```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];

// Basic slicing
var citrus = fruits.slice(1, 3);
console.log(citrus); // ["Banana", "Orange"]

// Slicing with negative indices
var lastTwo = fruits.slice(-2);
console.log(lastTwo); // ["Mango", "Pineapple"]

// Slicing from a start index to the end
var slicedFromIndex = fruits.slice(2);
console.log(slicedFromIndex); // ["Orange", "Mango", "Pineapple"]

// Cloning an array using slice
var clonedFruits = fruits.slice();
console.log(clonedFruits); // ["Apple", "Banana", "Orange", "Mango", "Pineapple"]
```

### splice()
Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.
```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];
var removed = fruits.splice(1, 2, "Grapes", "Pineapple");
console.log(removed); // ["Banana", "Orange"]
console.log(fruits); // ["Apple", "Grapes", "Pineapple", "Mango"]
```

### concat()
Merges two or more arrays. This method does not change the existing arrays but returns a new array.
```javascript
var array1 = [1, 2, 3];
var array2 = [4, 5, 6];
var combined = array1.concat(array2);
console.log(combined); // [1, 2, 3, 4, 5, 6]
```

### join()
Joins all elements of an array into a string. You can specify a separator, which defaults to a comma if none is provided.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
var string = fruits.join(", ");
console.log(string); // "Apple, Banana, Orange"
```

### reverse()
Reverses the order of the elements in an array. The first array element becomes the last, and the last becomes the first.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
fruits.reverse();
console.log(fruits); // ["Orange", "Banana", "Apple"]
```

### sort()
Sorts the elements of an array in place and returns the array. The default sort order is ascending, built upon converting the elements into strings.
```javascript
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.sort();
console.log(fruits); // ["Apple", "Banana", "Mango", "Orange"]

var numbers = [4, 2, 5, 1, 3];
numbers.sort(function(a, b) {
    return a - b;
});
console.log(numbers); // [1, 2, 3, 4, 5]
```

### indexOf()
Returns the first index at which a given element can be found in the array, or -1 if it is not present.
```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];
var index = fruits.indexOf("Banana");
console.log(index); // 1
```

### lastIndexOf()
Returns the last index at which a given element can be found in the array, or -1 if it is not present. The array is searched backwards, starting at `fromIndex`.
```javascript
var numbers = [2, 5, 9, 2];
var index = numbers.lastIndexOf(2);
console.log(index); // 3
```

### forEach()
Executes a provided function once for each array element.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
fruits.forEach(function(fruit, index) {
    console.log(index + ": " + fruit);
});
// Output:
// 0: Apple
// 1: Banana
// 2: Orange
```

### map()
Creates a new array with the results of calling a provided function on every element in the calling array.
```javascript
var numbers = [1, 4, 9, 16];
var doubles = numbers.map(function(number) {
    return number * 2;
});
console.log(doubles); // [2, 8, 18, 32]
```

### filter()
Creates a new array with all elements that pass the test implemented by the provided function.
```javascript
var numbers = [1, 2, 3, 4, 5];
var evenNumbers = numbers.filter(function(number) {
    return number % 2 === 0;
});
console.log(evenNumbers); // [2, 4]
```

### reduce()
Executes a reducer function on each element of the array, resulting in a single output value.
```javascript
var numbers = [1, 2, 3, 4, 5];
var sum = numbers.reduce(function(total, number) {
    return total + number;
}, 0);
console.log(sum); // 15
```

### reduceRight()
Applies a function against an accumulator and each value of the array (from right-to-left) to reduce it to a single value.
```javascript
var numbers = [1, 2, 3, 4, 5];
var sum = numbers.reduceRight(function(total, number) {
    return total + number;
}, 0);
console.log(sum); // 15
```

### some()
Tests whether at least one element in the array passes the test implemented by the provided function. It returns a Boolean value. [More](some-and-every.md)
```javascript
var numbers = [1, 2, 3, 4, 5];
var hasEven = numbers.some(function(number) {
    return number % 2 === 0;
});
console.log(hasEven); // true
```

### every()
Tests whether all elements in the array pass the test implemented by the provided function. It returns a Boolean value. [More](some-and-every.md)
```javascript
var numbers = [2, 4, 6, 8];
var allEven = numbers.every(function(number) {
    return number % 2 === 0;
});
console.log(allEven); // true
```

### find()
Returns the value of the first element in the provided array that satisfies the provided testing function. Otherwise, `undefined` is returned.
```javascript
var numbers = [1, 2, 3, 4, 5];
var found = numbers.find(function(number) {
    return number > 3;
});
console.log(found); // 4
```

### findIndex()
Returns the index of the first element in the array that satisfies the provided testing function. Otherwise, -1 is returned.
```javascript
var numbers = [1, 2, 3, 4, 5];
var index = numbers.findIndex(function(number) {
    return number > 3;
});
console.log(index); // 3
```

### isArray()
Determines whether the passed value is an array.
```javascript
var numbers = [1, 2, 3];
var result = Array.isArray(numbers);
console.log(result); // true

var notAnArray = "Hello";
console.log(Array.isArray(notAnArray)); // false
```

### toString()
Returns a string representing the array and its elements.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
var result = fruits.toString();
console.log(result); // "Apple,Banana

,Orange"
```

### valueOf()
Returns the array itself.
```javascript
var fruits = ["Apple", "Banana", "Orange"];
var result = fruits.valueOf();
console.log(result); // ["Apple", "Banana", "Orange"]
```

## Loops, Objects, and Arrays

### Looping Through an Array
```javascript
var fruits = ["Apple", "Banana", "Orange", "Mango"];

// Using a for loop
for (var i = 0; i < fruits.length; i++) {
    console.log(fruits[i]);
}

// Using a for...of loop
for (var fruit of fruits) {
    console.log(fruit);
}

// Using forEach method
fruits.forEach(function(fruit, index) {
    console.log(index + ": " + fruit);
});
```

### Looping Through an Object
```javascript
var person = {
    name: "John",
    age: 30,
    city: "New York"
};

// Using for...in loop
for (var key in person) {
    console.log(key + ": " + person[key]);
}
```

### Nested Loops
```javascript
var matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

for (var i = 0; i < matrix.length; i++) {
    for (var j = 0; j < matrix[i].length; j++) {
        console.log(matrix[i][j]);
    }
}
```

### Object Creation and Access
```javascript
var car = {
    make: "Toyota",
    model: "Camry",
    year: 2020,
    getCarInfo: function() {
        return this.make + " " + this.model + " (" + this.year + ")";
    }
};

console.log(car.make); // "Toyota"
console.log(car["model"]); // "Camry"
console.log(car.getCarInfo()); // "Toyota Camry (2020)"
```

### Array Manipulation
```javascript
var fruits = ["Apple", "Banana", "Orange"];

// Adding an item
fruits.push("Mango");
console.log(fruits); // ["Apple", "Banana", "Orange", "Mango"]

// Removing the last item
fruits.pop();
console.log(fruits); // ["Apple", "Banana", "Orange"]
```

## Advanced JavaScript Examples

### Higher-Order Functions
```javascript
function multiplyBy(factor) {
    return function(number) {
        return number * factor;
    };
}

var double = multiplyBy(2);
var triple = multiplyBy(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

### Currying
```javascript
function add(a) {
    return function(b) {
        return function(c) {
            return a + b + c;
        };
    };
}

var result = add(1)(2)(3);
console.log(result); // 6
```

### Debouncing
```javascript
function debounce(func, delay) {
    var timeoutId;
    return function() {
        clearTimeout(timeoutId);
        timeoutId = setTimeout(func, delay);
    };
}

var logMessage = debounce(function() {
    console.log("Debounced!");
}, 1000);

window.addEventListener("resize", logMessage);
```

### Throttling
```javascript
function throttle(func, limit) {
    var inThrottle;
    return function() {
        if (!inThrottle) {
            func.apply(this, arguments);
            inThrottle = true;
            setTimeout(function() {
                inThrottle = false;
            }, limit);
        }
    };
}

var logMessage = throttle(function() {
    console.log("Throttled!");
}, 1000);

window.addEventListener("scroll", logMessage);
```

### Event Delegation
```javascript
document.querySelector("#parent").addEventListener("click", function(event) {
    if (event.target && event.target.matches("li.item")) {
        console.log("Item clicked: " + event.target.textContent);
    }
});

// HTML Structure
// <ul id="parent">
//   <li class="item">Item 1</li>
//   <li class="item">Item 2</li>
//   <li class="item">Item 3</li>
// </ul>
```

### Promise Chaining
```javascript
function fetchData() {
    return new Promise(function(resolve) {
        setTimeout(function() {
            resolve("Data fetched");
        }, 1000);
    });
}

fetchData()
    .then(function(data) {
        console.log(data);
        return "Processing data";
    })
    .then(function(message) {
        console.log(message);
        return "Data processed";
    })
    .then(function(result) {
        console.log(result);
    });
```

### Dynamic Imports
```javascript
document.getElementById("loadModule").addEventListener("click", function() {
    import("./myModule.js").then(function(module) {
        module.myFunction();
    });
});

// myModule.js
export function myFunction() {
    console.log("Module loaded dynamically!");
}
```

### Generators
```javascript
function* idGenerator() {
    var id = 1;
    while (true) {
        yield id++;
    }
}

var generator = idGenerator();

console.log(generator.next().value); // 1
console.log(generator.next().value); // 2
console.log(generator.next().value); // 3
```

### Proxy Object
```javascript
var person = {
    name: "Alice",
    age: 25
};

var handler = {
    get: function(target, prop) {
        return prop in target ? target[prop] : "Property does not exist";
    },
    set: function(target, prop, value) {
        if (prop === "age" && value < 0) {
            console.log("Age cannot be negative");
        } else {
            target[prop] = value;
        }
    }
};

var proxyPerson = new Proxy(person, handler);

console.log(proxyPerson.name); // "Alice"
console.log(proxyPerson.gender); // "Property does not exist"

proxyPerson.age = -5; // "Age cannot be negative"
proxyPerson.age = 30;
console.log(proxyPerson.age); // 30
```

### Closures with Private Variables
```javascript
function createCounter() {
    var count = 0;

    return {
        increment: function() {
            count++;
            console.log(count);
        },
        decrement: function() {
            count--;
            console.log(count);
        },
        getCount: function() {
            return count;
        }
    };
}

var counter = createCounter();
counter.increment(); // 1
counter.increment(); // 2
counter.decrement(); // 1
console.log(counter.getCount()); // 1
```

### Custom Error Handling
```javascript
class CustomError extends Error {
    constructor(message) {
        super(message);
        this.name = "CustomError";
    }
}

try {
    throw new CustomError("Something went wrong");
} catch (error) {
    console.log(error.name + ": " + error.message);
}
```

### Async Iterators
```javascript
async function* asyncGenerator() {
    for (var i = 1; i <= 3; i++) {
        await new Promise(function(resolve) {
            setTimeout(resolve, 1000);
        });
        yield i;
    }
}

(async function() {
    for await (var value of asyncGenerator()) {
        console.log(value); // Logs 1, 2, 3 at one-second intervals
    }
})();
```

### Memoization
```javascript
function memoize(fn) {
    var cache = {};
    return function() {
        var key = JSON.stringify(arguments);
        if (cache[key]) {
            return cache[key];
        } else {
            var result = fn.apply(this, arguments);
            cache[key] = result;
            return result;
        }
    };
}

function slowFunction(num) {
    console.log("Computing...");
    return num * num;
}

var memoizedFunction = memoize(slowFunction);

console.log(memoizedFunction(5)); // "Computing..." 25
console.log(memoizedFunction(5)); // 25 (cached)
```

### Template Literals
```javascript
var user = {
    name: "Alice",
    age: 25,
    city: "New York"
};

var message = `Hello, my name is ${user.name}, I am ${user.age} years old and I live in ${user.city}.`;

console.log(message); // "Hello, my name is Alice, I am 25 years old and I live in New York."
```

### Destructuring Assignment
```javascript
var person = {
    name: "John",
    age: 30,
    address: {
        city: "Los Angeles",
        state: "California"
    }
};

var { name, age, address: { city } } = person;

console.log(name); // "John"
console.log(age); // 30
console.log(city); // "Los Angeles"
```

### Promises
A `Promise` is an object representing the eventual completion or failure of an asynchronous operation. [More](Promise.md)
```javascript
function fetchData() {
    return new Promise(function(resolve, reject) {
        var success = true;
        setTimeout(function() {
            if (success) {
                resolve("Data fetched successfully");
            } else {
                reject("Error fetching data");
            }
        }, 1000);
    });
}

fetchData()
    .then(function(result) {
        console.log(result); // "Data fetched successfully"
    })
    .catch(function(error) {
        console.log

(error);
    });
```

### Async/Await
`async/await` is a syntax for working with promises in a cleaner, more readable way.
```javascript
async function fetchData() {
    try {
        var result = await new Promise(function(resolve) {
            setTimeout(function() {
                resolve("Data fetched successfully");
            }, 1000);
        });
        console.log(result); // "Data fetched successfully"
    } catch (error) {
        console.log(error);
    }
}

fetchData();
```

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
### Shallow Copy and Deep Copy
- **Shallow Copy**: Copies the top-level properties, but nested objects or arrays are still referenced, not copied.

```javascript
var original = { name: "John", age: 30, address: { city: "New York" } };

// Shallow copy using Object.assign()
var shallowCopy = Object.assign({}, original);
shallowCopy.name = "Jane";
shallowCopy.address.city = "Los Angeles";

console.log(original.name); // "John" (not affected)
console.log(original.address.city); // "Los Angeles" (affected because of shallow copy)
```

- **Deep Copy**: Copies all levels of the object or array, creating a completely independent clone.

```javascript
var original = { name: "John", age: 30, address: { city: "New York" } };

// Deep copy using JSON methods
var deepCopy = JSON.parse(JSON.stringify(original));
deepCopy.name = "Jane";
deepCopy.address.city = "Los Angeles";

console.log(original.name); // "John" (not affected)
console.log(original.address.city); // "New York" (not affected)
```
