[Back to main](README.md#more-topic)

Below are examples of common JavaScript events and how they can be used in both plain JavaScript, React.js, and TypeScript.

### **1. `setTimeout` Example**

`setTimeout` is used to execute a function after a specified delay.

#### **1.1. JavaScript Example**

```javascript
// JavaScript Example
setTimeout(() => {
    console.log("This message is delayed by 2 seconds");
}, 2000);
```

#### **1.2. React Example**

In a React component, you can use `setTimeout` inside `useEffect` to delay an action.

```javascript
// React.js Example
import React, { useEffect } from 'react';

const DelayedMessage = () => {
    useEffect(() => {
        const timer = setTimeout(() => {
            console.log("This message is delayed by 2 seconds");
        }, 2000);

        return () => clearTimeout(timer); // Cleanup on unmount
    }, []);

    return <div>Check the console after 2 seconds.</div>;
};

export default DelayedMessage;
```

#### **1.3. TypeScript Example**

In TypeScript, you can use `setTimeout` similarly, but with type annotations.

```typescript
// TypeScript Example
import React, { useEffect } from 'react';

const DelayedMessage: React.FC = () => {
    useEffect(() => {
        const timer: NodeJS.Timeout = setTimeout(() => {
            console.log("This message is delayed by 2 seconds");
        }, 2000);

        return () => clearTimeout(timer); // Cleanup on unmount
    }, []);

    return <div>Check the console after 2 seconds.</div>;
};

export default DelayedMessage;
```

### **2. Scroll to Top Example**

The following examples demonstrate how to scroll the window to the top.

#### **2.1. JavaScript Example**

```javascript
// JavaScript Example
function scrollToTop() {
    window.scrollTo({
        top: 0,
        behavior: 'smooth'
    });
}

// Use the function
scrollToTop();
```

#### **2.2. React Example**

In a React component, you can create a button that scrolls the page to the top when clicked.

```javascript
// React.js Example
import React from 'react';

const ScrollToTopButton = () => {
    const scrollToTop = () => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
    };

    return <button onClick={scrollToTop}>Scroll to Top</button>;
};

export default ScrollToTopButton;
```

#### **2.3. TypeScript Example**

With TypeScript, you can add type annotations to ensure type safety.

```typescript
// TypeScript Example
import React from 'react';

const ScrollToTopButton: React.FC = () => {
    const scrollToTop = (): void => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
    };

    return <button onClick={scrollToTop}>Scroll to Top</button>;
};

export default ScrollToTopButton;
```

### **3. `setInterval` Example**

`setInterval` is used to execute a function repeatedly with a fixed time delay between each call.

#### **3.1. JavaScript Example**

```javascript
// JavaScript Example
setInterval(() => {
    console.log("This message logs every 3 seconds");
}, 3000);
```

#### **3.2. React Example**

In React, you can use `setInterval` inside `useEffect` to create a timer or similar functionality.

```javascript
// React.js Example
import React, { useEffect, useState } from 'react';

const Timer = () => {
    const [count, setCount] = useState(0);

    useEffect(() => {
        const interval = setInterval(() => {
            setCount(prevCount => prevCount + 1);
        }, 1000);

        return () => clearInterval(interval); // Cleanup on unmount
    }, []);

    return <div>Count: {count}</div>;
};

export default Timer;
```

#### **3.3. TypeScript Example**

With TypeScript, you can use `setInterval` with proper type annotations.

```typescript
// TypeScript Example
import React, { useEffect, useState } from 'react';

const Timer: React.FC = () => {
    const [count, setCount] = useState<number>(0);

    useEffect(() => {
        const interval: NodeJS.Timeout = setInterval(() => {
            setCount(prevCount => prevCount + 1);
        }, 1000);

        return () => clearInterval(interval); // Cleanup on unmount
    }, []);

    return <div>Count: {count}</div>;
};

export default Timer;
```

### **4. Handling Window Resize Event**

You may want to execute some code whenever the window is resized.

#### **4.1. JavaScript Example**

```javascript
// JavaScript Example
window.addEventListener('resize', () => {
    console.log(`Window width: ${window.innerWidth}, height: ${window.innerHeight}`);
});
```

#### **4.2. React Example**

In React, use `useEffect` to handle window resize events.

```javascript
// React.js Example
import React, { useEffect, useState } from 'react';

const WindowSize = () => {
    const [size, setSize] = useState({
        width: window.innerWidth,
        height: window.innerHeight
    });

    useEffect(() => {
        const handleResize = () => {
            setSize({
                width: window.innerWidth,
                height: window.innerHeight
            });
        };

        window.addEventListener('resize', handleResize);

        return () => window.removeEventListener('resize', handleResize); // Cleanup on unmount
    }, []);

    return (
        <div>
            Width: {size.width}, Height: {size.height}
        </div>
    );
};

export default WindowSize;
```

#### **4.3. TypeScript Example**

With TypeScript, ensure type safety by defining the shape of the state.

```typescript
// TypeScript Example
import React, { useEffect, useState } from 'react';

interface Size {
    width: number;
    height: number;
}

const WindowSize: React.FC = () => {
    const [size, setSize] = useState<Size>({
        width: window.innerWidth,
        height: window.innerHeight
    });

    useEffect(() => {
        const handleResize = (): void => {
            setSize({
                width: window.innerWidth,
                height: window.innerHeight
            });
        };

        window.addEventListener('resize', handleResize);

        return () => window.removeEventListener('resize', handleResize); // Cleanup on unmount
    }, []);

    return (
        <div>
            Width: {size.width}, Height: {size.height}
        </div>
    );
};

export default WindowSize;
```

### **5. Handling Mouse Events**

You may want to handle mouse events such as `click` or `mousemove`.

#### **5.1. JavaScript Example**

```javascript
// JavaScript Example
document.addEventListener('click', (event) => {
    console.log(`Mouse clicked at: X=${event.clientX}, Y=${event.clientY}`);
});
```

#### **5.2. React Example**

In React, you can handle mouse events using the `onClick` or `onMouseMove` props.

```javascript
// React.js Example
import React from 'react';

const ClickLogger = () => {
    const handleClick = (event) => {
        console.log(`Mouse clicked at: X=${event.clientX}, Y=${event.clientY}`);
    };

    return <div onClick={handleClick} style={{ height: '100vh', border: '1px solid black' }}>Click anywhere</div>;
};

export default ClickLogger;
```

#### **5.3. TypeScript Example**

In TypeScript, use type annotations for event handlers.

```typescript
// TypeScript Example
import React from 'react';

const ClickLogger: React.FC = () => {
    const handleClick = (event: React.MouseEvent<HTMLDivElement, MouseEvent>): void => {
        console.log(`Mouse clicked at: X=${event.clientX}, Y=${event.clientY}`);
    };

    return <div onClick={handleClick} style={{ height: '100vh', border: '1px solid black' }}>Click anywhere</div>;
};

export default ClickLogger;
```



### **6. `DOMContentLoaded` Event**

The `DOMContentLoaded` event is fired when the initial HTML document has been completely loaded and parsed, without waiting for stylesheets, images, and subframes to finish loading.

#### **6.1. JavaScript Example**

```javascript
// JavaScript Example
document.addEventListener('DOMContentLoaded', () => {
    console.log('DOM fully loaded and parsed');
});
```

#### **6.2. React Example**

In React, you generally don't need to use `DOMContentLoaded` since React handles rendering once the DOM is ready. However, for educational purposes:

```javascript
// React.js Example
import React, { useEffect } from 'react';

const DOMLoaded = () => {
    useEffect(() => {
        const handleDOMContentLoaded = () => {
            console.log('DOM fully loaded and parsed');
        };

        document.addEventListener('DOMContentLoaded', handleDOMContentLoaded);

        return () => document.removeEventListener('DOMContentLoaded', handleDOMContentLoaded);
    }, []);

    return <div>DOM Content Loaded Example</div>;
};

export default DOMLoaded;
```

#### **6.3. TypeScript Example**

```typescript
// TypeScript Example
import React, { useEffect } from 'react';

const DOMLoaded: React.FC = () => {
    useEffect(() => {
        const handleDOMContentLoaded = (): void => {
            console.log('DOM fully loaded and parsed');
        };

        document.addEventListener('DOMContentLoaded', handleDOMContentLoaded);

        return () => document.removeEventListener('DOMContentLoaded', handleDOMContentLoaded);
    }, []);

    return <div>DOM Content Loaded Example</div>;
};

export default DOMLoaded;
```

### **7. `focus` and `blur` Events**

The `focus` event is fired when an element gains focus, and `blur` is fired when it loses focus.

#### **7.1. JavaScript Example**

```javascript
// JavaScript Example
const input = document.getElementById('myInput');

input.addEventListener('focus', () => {
    console.log('Input is focused');
});

input.addEventListener('blur', () => {
    console.log('Input lost focus');
});
```

#### **7.2. React Example**

In React, you can use the `onFocus` and `onBlur` props to handle these events.

```javascript
// React.js Example
import React from 'react';

const FocusBlurExample = () => {
    const handleFocus = () => {
        console.log('Input is focused');
    };

    const handleBlur = () => {
        console.log('Input lost focus');
    };

    return <input onFocus={handleFocus} onBlur={handleBlur} placeholder="Click to focus" />;
};

export default FocusBlurExample;
```

#### **7.3. TypeScript Example**

```typescript
// TypeScript Example
import React from 'react';

const FocusBlurExample: React.FC = () => {
    const handleFocus = (): void => {
        console.log('Input is focused');
    };

    const handleBlur = (): void => {
        console.log('Input lost focus');
    };

    return <input onFocus={handleFocus} onBlur={handleBlur} placeholder="Click to focus" />;
};

export default FocusBlurExample;
```

### **8. `input` and `change` Events**

The `input` event is fired every time the value of an `<input>`, `<textarea>`, or `<select>` element changes. The `change` event is fired when the element loses focus after its value was changed.

#### **8.1. JavaScript Example**

```javascript
// JavaScript Example
const input = document.getElementById('myInput');

input.addEventListener('input', (event) => {
    console.log('Input value changed to:', event.target.value);
});

input.addEventListener('change', (event) => {
    console.log('Input value confirmed to:', event.target.value);
});
```

#### **8.2. React Example**

In React, you can handle these events using `onInput` and `onChange` props.

```javascript
// React.js Example
import React, { useState } from 'react';

const InputChangeExample = () => {
    const [value, setValue] = useState('');

    const handleInput = (event) => {
        setValue(event.target.value);
        console.log('Input value changed to:', event.target.value);
    };

    const handleChange = (event) => {
        console.log('Input value confirmed to:', event.target.value);
    };

    return <input value={value} onInput={handleInput} onChange={handleChange} placeholder="Type something" />;
};

export default InputChangeExample;
```

#### **8.3. TypeScript Example**

```typescript
// TypeScript Example
import React, { useState } from 'react';

const InputChangeExample: React.FC = () => {
    const [value, setValue] = useState<string>('');

    const handleInput = (event: React.ChangeEvent<HTMLInputElement>): void => {
        setValue(event.target.value);
        console.log('Input value changed to:', event.target.value);
    };

    const handleChange = (event: React.ChangeEvent<HTMLInputElement>): void => {
        console.log('Input value confirmed to:', event.target.value);
    };

    return <input value={value} onInput={handleInput} onChange={handleChange} placeholder="Type something" />;
};

export default InputChangeExample;
```

### **9. `keydown`, `keyup`, and `keypress` Events**

These events are fired when a key is pressed down, released, or while it is pressed.

#### **9.1. JavaScript Example**

```javascript
// JavaScript Example
document.addEventListener('keydown', (event) => {
    console.log('Key pressed:', event.key);
});

document.addEventListener('keyup', (event) => {
    console.log('Key released:', event.key);
});
```

#### **9.2. React Example**

In React, you can handle these events using `onKeyDown`, `onKeyUp`, and `onKeyPress` props.

```javascript
// React.js Example
import React from 'react';

const KeyPressExample = () => {
    const handleKeyDown = (event) => {
        console.log('Key pressed:', event.key);
    };

    const handleKeyUp = (event) => {
        console.log('Key released:', event.key);
    };

    return <input onKeyDown={handleKeyDown} onKeyUp={handleKeyUp} placeholder="Press any key" />;
};

export default KeyPressExample;
```

#### **9.3. TypeScript Example**

```typescript
// TypeScript Example
import React from 'react';

const KeyPressExample: React.FC = () => {
    const handleKeyDown = (event: React.KeyboardEvent<HTMLInputElement>): void => {
        console.log('Key pressed:', event.key);
    };

    const handleKeyUp = (event: React.KeyboardEvent<HTMLInputElement>): void => {
        console.log('Key released:', event.key);
    };

    return <input onKeyDown={handleKeyDown} onKeyUp={handleKeyUp} placeholder="Press any key" />;
};

export default KeyPressExample;
```

### **10. `mouseover` and `mouseout` Events**

The `mouseover` event is fired when the mouse pointer enters an element, and `mouseout` is fired when it leaves the element.

#### **10.1. JavaScript Example**

```javascript
// JavaScript Example
const element = document.getElementById('myElement');

element.addEventListener('mouseover', () => {
    console.log('Mouse is over the element');
});

element.addEventListener('mouseout', () => {
    console.log('Mouse left the element');
});
```

#### **10.2. React Example**

In React, you can handle these events using `onMouseOver` and `onMouseOut` props.

```javascript
// React.js Example
import React from 'react';

const MouseOverOutExample = () => {
    const handleMouseOver = () => {
        console.log('Mouse is over the element');
    };

    const handleMouseOut = () => {
        console.log('Mouse left the element');
    };

    return (
        <div onMouseOver={handleMouseOver} onMouseOut={handleMouseOut} style={{ padding: '20px', border: '1px solid black' }}>
            Hover over this box
        </div>
    );
};

export default MouseOverOutExample;
```

#### **10.3. TypeScript Example**

```typescript
// TypeScript Example
import React from 'react';

const MouseOverOutExample: React.FC = () => {
    const handleMouseOver = (): void => {
        console.log('Mouse is over the element');
    };

    const handleMouseOut = (): void => {
        console.log('Mouse left the element');
    };

    return (
        <div onMouseOver={handleMouseOver} onMouseOut={handleMouseOut} style={{ padding: '20px', border: '1px solid black' }}>
            Hover over this box
        </div>
    );
};

export default MouseOverOutExample;
```

### **11. `contextmenu` Event**

The `contextmenu` event is fired when the right mouse button is clicked, which usually opens a context menu.

#### **11.1. JavaScript Example**

```javascript
// JavaScript Example
document.addEventListener('contextmenu', (event) => {
    event.preventDefault(); // Prevent the context menu from appearing
    console.log('Right-click detected

');
});
```

#### **11.2. React Example**

In React, you can handle the `contextmenu` event using the `onContextMenu` prop.

```javascript
// React.js Example
import React from 'react';

const ContextMenuExample = () => {
    const handleContextMenu = (event) => {
        event.preventDefault(); // Prevent the context menu from appearing
        console.log('Right-click detected');
    };

    return (
        <div onContextMenu={handleContextMenu} style={{ padding: '20px', border: '1px solid black' }}>
            Right-click anywhere in this box
        </div>
    );
};

export default ContextMenuExample;
```

#### **11.3. TypeScript Example**

```typescript
// TypeScript Example
import React from 'react';

const ContextMenuExample: React.FC = () => {
    const handleContextMenu = (event: React.MouseEvent<HTMLDivElement, MouseEvent>): void => {
        event.preventDefault(); // Prevent the context menu from appearing
        console.log('Right-click detected');
    };

    return (
        <div onContextMenu={handleContextMenu} style={{ padding: '20px', border: '1px solid black' }}>
            Right-click anywhere in this box
        </div>
    );
};

export default ContextMenuExample;
```

### **12. `submit` Event**

The `submit` event is fired when a form is submitted.

#### **12.1. JavaScript Example**

```javascript
// JavaScript Example
const form = document.getElementById('myForm');

form.addEventListener('submit', (event) => {
    event.preventDefault(); // Prevent the form from submitting
    console.log('Form submitted');
});
```

#### **12.2. React Example**

In React, you can handle form submission using the `onSubmit` prop.

```javascript
// React.js Example
import React from 'react';

const FormSubmitExample = () => {
    const handleSubmit = (event) => {
        event.preventDefault(); // Prevent the form from submitting
        console.log('Form submitted');
    };

    return (
        <form onSubmit={handleSubmit}>
            <input type="text" placeholder="Enter something" />
            <button type="submit">Submit</button>
        </form>
    );
};

export default FormSubmitExample;
```

#### **12.3. TypeScript Example**

```typescript
// TypeScript Example
import React from 'react';

const FormSubmitExample: React.FC = () => {
    const handleSubmit = (event: React.FormEvent<HTMLFormElement>): void => {
        event.preventDefault(); // Prevent the form from submitting
        console.log('Form submitted');
    };

    return (
        <form onSubmit={handleSubmit}>
            <input type="text" placeholder="Enter something" />
            <button type="submit">Submit</button>
        </form>
    );
};

export default FormSubmitExample;
```
