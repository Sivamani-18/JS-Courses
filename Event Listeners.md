[Back to main](README.md#more-topic)

Below are examples related to adding and removing event listeners, handling window resize events, and managing component lifecycle events such as mounting and unmounting in a React component.

### **1. Handling Window Resize Events**

This example demonstrates how to add an event listener for the `resize` event and remove it when it's no longer needed.

```javascript
// JavaScript Example

function handleResize() {
    console.log(`Window resized to ${window.innerWidth}x${window.innerHeight}`);
}

// Add event listener for resize
window.addEventListener('resize', handleResize);

// Remove event listener (when no longer needed)
window.removeEventListener('resize', handleResize);
```

### **2. Adding and Removing Event Listeners**

This example demonstrates how to add and remove a click event listener on a button.

```javascript
// JavaScript Example

function handleClick() {
    console.log('Button clicked!');
}

const button = document.getElementById('myButton');

// Add event listener
button.addEventListener('click', handleClick);

// Remove event listener
button.removeEventListener('click', handleClick);
```

### **3. Handling Component Mounting and Unmounting in React**

This example demonstrates how to add and remove event listeners when a React component mounts and unmounts.

```javascript
// React Example

import React, { useEffect } from 'react';

function MyComponent() {
    useEffect(() => {
        function handleResize() {
            console.log(`Window resized to ${window.innerWidth}x${window.innerHeight}`);
        }

        // Add event listener when the component mounts
        window.addEventListener('resize', handleResize);

        // Cleanup event listener when the component unmounts
        return () => {
            window.removeEventListener('resize', handleResize);
        };
    }, []); // Empty dependency array means this effect runs only on mount and unmount

    return (
        <div>
            <h1>Hello, world!</h1>
        </div>
    );
}

export default MyComponent;
```

### **4. Adding and Removing Dynamic Elements**

This example demonstrates how to dynamically add and remove DOM elements.

```javascript
// JavaScript Example

const container = document.getElementById('container');

// Create a new element
const newElement = document.createElement('div');
newElement.textContent = 'I am a new element';

// Add the new element to the container
container.appendChild(newElement);

// Remove the element from the container
container.removeChild(newElement);
```

### **5. Removing All Event Listeners from an Element**

This example shows how to remove all event listeners from an element by cloning it and replacing the original element.

```javascript
// JavaScript Example

const button = document.getElementById('myButton');

function handleClick() {
    console.log('Button clicked!');
}

button.addEventListener('click', handleClick);

// Remove all event listeners by cloning the element
const newButton = button.cloneNode(true);
button.parentNode.replaceChild(newButton, button);

// Now, newButton does not have any event listeners attached
newButton.addEventListener('click', () => {
    console.log('New button clicked!');
});
```

### **6. Adding Event Listeners Conditionally in React**

This React example demonstrates how to conditionally add or remove an event listener based on a component's state.

```javascript
// React Example

import React, { useState, useEffect } from 'react';

function ToggleEventListener() {
    const [isListening, setIsListening] = useState(false);

    useEffect(() => {
        function handleClick() {
            console.log('Document clicked!');
        }

        if (isListening) {
            document.addEventListener('click', handleClick);
        } else {
            document.removeEventListener('click', handleClick);
        }

        // Cleanup on unmount
        return () => {
            document.removeEventListener('click', handleClick);
        };
    }, [isListening]);

    return (
        <div>
            <button onClick={() => setIsListening(!isListening)}>
                {isListening ? 'Stop Listening' : 'Start Listening'}
            </button>
        </div>
    );
}

export default ToggleEventListener;
```
