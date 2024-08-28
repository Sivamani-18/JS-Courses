[Back to main](README.md#more-topic)

Below is the same example using TypeScript. This will demonstrate how to set up a React application with the Context API and TypeScript.

### **1. Setting Up the Context with TypeScript**

We'll start by creating a context that holds the theme value.

#### **1.1. Creating the `ThemeContext` with TypeScript**

```typescript
// ThemeContext.tsx

import React, { createContext, useState, ReactNode } from 'react';

// Define the shape of the context value
interface ThemeContextType {
    theme: string;
    toggleTheme: () => void;
}

// Create the context with a default value
export const ThemeContext = createContext<ThemeContextType | undefined>(undefined);

// Define the props for the provider component
interface ThemeProviderProps {
    children: ReactNode;
}

// Create the provider component
export const ThemeProvider: React.FC<ThemeProviderProps> = ({ children }) => {
    const [theme, setTheme] = useState<string>('light'); // default theme is 'light'

    const toggleTheme = () => {
        setTheme((prevTheme) => (prevTheme === 'light' ? 'dark' : 'light'));
    };

    return (
        <ThemeContext.Provider value={{ theme, toggleTheme }}>
            {children}
        </ThemeContext.Provider>
    );
};
```

### **2. Creating Components to Use the Context with TypeScript**

We'll create two components: one that displays the current theme and one that toggles the theme.

#### **2.1. Creating the `ThemeDisplay` Component**

This component will display the current theme.

```typescript
// ThemeDisplay.tsx

import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

const ThemeDisplay: React.FC = () => {
    const themeContext = useContext(ThemeContext);

    if (!themeContext) {
        return <div>Error: ThemeContext is not defined</div>;
    }

    return (
        <div>
            <h1>Current Theme: {themeContext.theme}</h1>
        </div>
    );
};

export default ThemeDisplay;
```

#### **2.2. Creating the `ThemeToggle` Component**

This component will have a button to toggle between light and dark themes.

```typescript
// ThemeToggle.tsx

import React, { useContext } from 'react';
import { ThemeContext } from './ThemeContext';

const ThemeToggle: React.FC = () => {
    const themeContext = useContext(ThemeContext);

    if (!themeContext) {
        return <div>Error: ThemeContext is not defined</div>;
    }

    return (
        <button onClick={themeContext.toggleTheme}>Toggle Theme</button>
    );
};

export default ThemeToggle;
```

### **3. Using the Context in the App Component**

Now, wrap your application with the `ThemeProvider` and use the components.

```typescript
// App.tsx

import React from 'react';
import { ThemeProvider } from './ThemeContext';
import ThemeDisplay from './ThemeDisplay';
import ThemeToggle from './ThemeToggle';

const App: React.FC = () => {
    return (
        <ThemeProvider>
            <div>
                <ThemeDisplay />
                <ThemeToggle />
            </div>
        </ThemeProvider>
    );
};

export default App;
```

### **4. Explanation**

- **Type Definitions**:
  - `ThemeContextType`: Defines the shape of the context value, including the `theme` string and `toggleTheme` function.
  - `ThemeProviderProps`: Defines the props for the `ThemeProvider` component, specifically expecting `children` of type `ReactNode`.
  
- **ThemeContext (`ThemeContext.tsx`)**: 
  - We create a `ThemeContext` using `createContext<ThemeContextType | undefined>()` and provide a default value of `undefined`.
  - The `ThemeProvider` component manages the theme state and provides a `toggleTheme` function. It wraps the context provider around its children.
  
- **ThemeDisplay (`ThemeDisplay.tsx`)**: 
  - This component consumes the `ThemeContext` to display the current theme. It handles the case where the context might be `undefined` (though in this simple example, this shouldn't occur).
  
- **ThemeToggle (`ThemeToggle.tsx`)**:
  - This component consumes the `ThemeContext` and provides a button to toggle the theme. It also checks for `undefined` to handle the case where the context might not be available.

- **App (`App.tsx`)**:
  - The `ThemeProvider` wraps the entire application, making the theme state and toggle function available to all nested components.

### **5. Running the Application**

If you are using `create-react-app` with TypeScript, you can run the application with:

```bash
npm start
```

### **6. Result**

When you run the application:

- The `ThemeDisplay` component will initially show "Current Theme: light".
- The `ThemeToggle` component provides a button labeled "Toggle Theme".
- When you click the "Toggle Theme" button, the theme switches between "light" and "dark", and the `ThemeDisplay` component updates to reflect the new theme.
