Here are more examples demonstrating the usage of the `some()` and `every()` methods in JavaScript.

### **1. `some()` Examples**

#### **1.1. Checking if an Array Contains Any Even Numbers**
This example checks if there is at least one even number in the array.
```javascript
const numbers = [1, 3, 5, 7, 8];

const hasEvenNumber = numbers.some(function(number) {
    return number % 2 === 0;
});

console.log(hasEvenNumber); // true (because 8 is even)
```

#### **1.2. Checking if Any String in an Array Contains a Specific Character**
This example checks if any string in the array contains the letter "a".
```javascript
const words = ["hello", "world", "javascript", "developer"];

const containsA = words.some(function(word) {
    return word.includes("a");
});

console.log(containsA); // true (because "javascript" contains "a")
```

#### **1.3. Checking if Any Object in an Array Meets a Condition**
This example checks if any object in the array has a property `age` greater than 30.
```javascript
const users = [
    { name: "Alice", age: 25 },
    { name: "Bob", age: 35 },
    { name: "Charlie", age: 28 }
];

const isAnyUserAbove30 = users.some(function(user) {
    return user.age > 30;
});

console.log(isAnyUserAbove30); // true (because Bob's age is 35)
```

#### **1.4. Checking if Any Item in a Shopping Cart is Out of Stock**
This example checks if any item in a shopping cart is out of stock.
```javascript
const cart = [
    { item: "Laptop", quantity: 1, inStock: true },
    { item: "Mouse", quantity: 2, inStock: true },
    { item: "Keyboard", quantity: 1, inStock: false }
];

const isAnyItemOutOfStock = cart.some(function(product) {
    return !product.inStock;
});

console.log(isAnyItemOutOfStock); // true (because the Keyboard is out of stock)
```

### **2. `every()` Examples**

#### **2.1. Checking if All Numbers in an Array Are Positive**
This example checks if all numbers in the array are positive.
```javascript
const numbers = [2, 4, 6, 8, 10];

const allPositive = numbers.every(function(number) {
    return number > 0;
});

console.log(allPositive); // true (because all numbers are positive)
```

#### **2.2. Checking if All Strings in an Array Are Shorter Than 10 Characters**
This example checks if all strings in the array are shorter than 10 characters.
```javascript
const words = ["hello", "world", "js", "code"];

const allShorterThan10 = words.every(function(word) {
    return word.length < 10;
});

console.log(allShorterThan10); // true (because all words are shorter than 10 characters)
```

#### **2.3. Checking if All Users Are Adults**
This example checks if all users in the array are 18 years or older.
```javascript
const users = [
    { name: "Alice", age: 25 },
    { name: "Bob", age: 35 },
    { name: "Charlie", age: 17 }
];

const allAreAdults = users.every(function(user) {
    return user.age >= 18;
});

console.log(allAreAdults); // false (because Charlie is 17)
```

#### **2.4. Checking if All Tasks in a To-Do List Are Completed**
This example checks if all tasks in a to-do list are marked as completed.
```javascript
const tasks = [
    { task: "Do the laundry", completed: true },
    { task: "Clean the house", completed: true },
    { task: "Buy groceries", completed: false }
];

const allTasksCompleted = tasks.every(function(task) {
    return task.completed;
});

console.log(allTasksCompleted); // false (because "Buy groceries" is not completed)
```

### **3. Combining `some()` and `every()`**

#### **3.1. Checking if a List of Products Has Both In-Stock and Out-of-Stock Items**
This example uses both `some()` and `every()` to check if the array has a mix of in-stock and out-of-stock items.
```javascript
const products = [
    { name: "Laptop", inStock: true },
    { name: "Mouse", inStock: false },
    { name: "Keyboard", inStock: true }
];

const hasInStock = products.some(function(product) {
    return product.inStock;
});

const hasOutOfStock = products.some(function(product) {
    return !product.inStock;
});

console.log(hasInStock); // true (because some products are in stock)
console.log(hasOutOfStock); // true (because some products are out of stock)

const hasMixedStockStatus = hasInStock && hasOutOfStock;
console.log(hasMixedStockStatus); // true (because there is a mix of in-stock and out-of-stock products)
```

#### **3.2. Checking if a List of Numbers is Either All Positive or Contains a Negative**
This example uses both `some()` and `every()` to determine the nature of the numbers in an array.
```javascript
const numbers = [3, 5, -1, 8, 10];

const allPositive = numbers.every(function(number) {
    return number > 0;
});

const hasNegative = numbers.some(function(number) {
    return number < 0;
});

console.log(allPositive); // false (because there is a negative number)
console.log(hasNegative); // true (because there is a negative number)
```
