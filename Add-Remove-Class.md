Below are some examples demonstrating how to add, remove, and toggle classes on elements, as well as other useful DOM manipulation methods.

### **1. Adding a Class to an Element**

This example demonstrates how to add a class to an HTML element using `classList.add()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Add a class
element.classList.add('active');

// The element now has the class "active"
```

### **2. Removing a Class from an Element**

This example demonstrates how to remove a class from an HTML element using `classList.remove()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Remove a class
element.classList.remove('active');

// The element no longer has the class "active"
```

### **3. Toggling a Class on an Element**

This example shows how to toggle a class on and off using `classList.toggle()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Toggle the class "active"
element.classList.toggle('active');

// If "active" was present, it's removed; if it wasn't, it's added
```

### **4. Checking if an Element Has a Class**

This example demonstrates how to check if an element has a specific class using `classList.contains()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Check if the element has the class "active"
const hasActiveClass = element.classList.contains('active');

console.log(hasActiveClass); // true or false
```

### **5. Replacing a Class on an Element**

This example demonstrates how to replace one class with another using `classList.replace()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Replace the class "inactive" with "active"
element.classList.replace('inactive', 'active');

// The element no longer has "inactive" and now has "active"
```

### **6. Adding Multiple Classes to an Element**

This example shows how to add multiple classes to an element at once.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Add multiple classes
element.classList.add('active', 'highlighted', 'visible');

// The element now has "active", "highlighted", and "visible"
```

### **7. Removing Multiple Classes from an Element**

This example demonstrates how to remove multiple classes from an element at once.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Remove multiple classes
element.classList.remove('active', 'highlighted', 'visible');

// The element no longer has "active", "highlighted", or "visible"
```

### **8. Manipulating the Style of an Element**

This example shows how to directly manipulate the inline styles of an element using the `style` property.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Set multiple styles
element.style.backgroundColor = 'blue';
element.style.color = 'white';
element.style.padding = '10px';

// The element now has these inline styles applied
```

### **9. Setting an Attribute on an Element**

This example demonstrates how to set an attribute on an HTML element using `setAttribute()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Set a custom attribute
element.setAttribute('data-custom', 'customValue');

// The element now has a "data-custom" attribute with the value "customValue"
```

### **10. Removing an Attribute from an Element**

This example shows how to remove an attribute from an HTML element using `removeAttribute()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Remove the "data-custom" attribute
element.removeAttribute('data-custom');

// The element no longer has the "data-custom" attribute
```

### **11. Getting the Value of an Attribute**

This example demonstrates how to get the value of an attribute using `getAttribute()`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Get the value of the "data-custom" attribute
const customValue = element.getAttribute('data-custom');

console.log(customValue); // "customValue" or null if the attribute doesn't exist
```

### **12. Adding and Removing Content from an Element**

This example shows how to manipulate the content inside an HTML element using `innerHTML` or `textContent`.

```javascript
// JavaScript Example

const element = document.getElementById('myElement');

// Set HTML content
element.innerHTML = '<strong>This is bold text</strong>';

// Set text content (no HTML parsing)
element.textContent = 'This is plain text';

// Append content to the existing content
element.innerHTML += '<p>Additional paragraph</p>';
```

### **13. Appending and Prepending Elements**

This example demonstrates how to add elements to the beginning or end of another element using `appendChild()`, `append()`, or `prepend()`.

```javascript
// JavaScript Example

const container = document.getElementById('container');

// Create a new element
const newElement = document.createElement('div');
newElement.textContent = 'I am a new element';

// Append the new element to the end of the container
container.appendChild(newElement);

// Or using append (can also add multiple nodes)
container.append(newElement, 'Some text');

// Prepend the new element to the beginning of the container
container.prepend(newElement);
```

### **14. Cloning an Element**

This example shows how to clone an element and optionally clone its children.

```javascript
// JavaScript Example

const originalElement = document.getElementById('myElement');

// Clone the element and its children
const clonedElement = originalElement.cloneNode(true);

// Add the cloned element to the DOM
document.body.appendChild(clonedElement);
```

### **15. Removing an Element from the DOM**

This example demonstrates how to remove an element from the DOM using `removeChild()` or `remove()`.

```javascript
// JavaScript Example

const parentElement = document.getElementById('parentElement');
const childElement = document.getElementById('childElement');

// Remove the child element using removeChild
parentElement.removeChild(childElement);

// Or directly remove the element using remove
childElement.remove();
```
