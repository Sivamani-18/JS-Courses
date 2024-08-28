[Back to main](README.md#more-topic)

Below is an example of how to use React's Context API to share state across components without having to pass props down manually at every level.

### **1. Setting Up Context**

We'll create a simple example where we have a `UserContext` that provides a user's information to multiple components.

### **2. Creating the Context**

First, create a context and a provider component.

#### **2.1. Creating the UserContext**

```javascript
// UserContext.js

import React, { createContext, useState } from 'react';

// Create a context
export const UserContext = createContext();

// Create a provider component
export const UserProvider = ({ children }) => {
    const [user, setUser] = useState({
        name: 'John Doe',
        email: 'john.doe@example.com'
    });

    return (
        <UserContext.Provider value={{ user, setUser }}>
            {children}
        </UserContext.Provider>
    );
};
```

### **3. Consuming the Context**

Now, create components that consume the context to display and update the user information.

#### **3.1. Creating a Header Component to Display the User's Name**

```javascript
// Header.js

import React, { useContext } from 'react';
import { UserContext } from './UserContext';

const Header = () => {
    const { user } = useContext(UserContext);

    return (
        <header>
            <h1>Welcome, {user.name}!</h1>
        </header>
    );
};

export default Header;
```

#### **3.2. Creating a Profile Component to Display User Details**

```javascript
// Profile.js

import React, { useContext } from 'react';
import { UserContext } from './UserContext';

const Profile = () => {
    const { user } = useContext(UserContext);

    return (
        <div>
            <h2>User Profile</h2>
            <p>Name: {user.name}</p>
            <p>Email: {user.email}</p>
        </div>
    );
};

export default Profile;
```

#### **3.3. Creating a Component to Update the User Information**

```javascript
// UpdateProfile.js

import React, { useContext } from 'react';
import { UserContext } from './UserContext';

const UpdateProfile = () => {
    const { user, setUser } = useContext(UserContext);

    const handleChangeName = () => {
        setUser({
            ...user,
            name: 'Jane Doe'
        });
    };

    return (
        <button onClick={handleChangeName}>Change Name to Jane Doe</button>
    );
};

export default UpdateProfile;
```

### **4. Using the Provider in the App Component**

Now, wrap your application with the `UserProvider` to provide the context to the components.

```javascript
// App.js

import React from 'react';
import { UserProvider } from './UserContext';
import Header from './Header';
import Profile from './Profile';
import UpdateProfile from './UpdateProfile';

function App() {
    return (
        <UserProvider>
            <div>
                <Header />
                <Profile />
                <UpdateProfile />
            </div>
        </UserProvider>
    );
}

export default App;
```

### **5. Explanation**

- **UserContext (`UserContext.js`)**: We create a `UserContext` using `createContext()`. The `UserProvider` component uses the `useState` hook to manage the user's state and provides this state along with a method to update it (`setUser`) to its children via `UserContext.Provider`.
  
- **Header (`Header.js`)**: The `Header` component consumes the `UserContext` to display the user's name.

- **Profile (`Profile.js`)**: The `Profile` component also consumes the `UserContext` to display more detailed user information (name and email).

- **UpdateProfile (`UpdateProfile.js`)**: The `UpdateProfile` component consumes the `UserContext` and provides a button to update the user's name. It uses the `setUser` function from the context to update the user's state.

- **App (`App.js`)**: The `UserProvider` wraps the entire application, making the user state and update function available to all nested components.

### **6. Running the Application**

If you're using a tool like `create-react-app`, you can run the application with:

```bash
npm start
```

### **7. Result**

When you run the application:

- The `Header` component displays a welcome message with the user's name.
- The `Profile` component shows the user's name and email.
- The `UpdateProfile` component provides a button to change the user's name to "Jane Doe".
- Clicking the button in `UpdateProfile` will update the context, and both the `Header` and `Profile` components will reflect the change immediately.
