Example that involves a name change, where the user’s name can be updated from "Siva" to "Sivamani" using `useContext` and `useReducer`. This simulates the process of updating the user's profile information.

### Step 1: Define the State and Action Types

```tsx
import React, { useReducer, createContext, useContext, ReactNode } from 'react';

// Define the state type for the user
type UserState = {
  name: string;
};

// Define action types for updating the user's name
type UserAction = { type: 'UPDATE_NAME'; payload: string };

// Initial state: user's initial name is 'Siva'
const initialState: UserState = { name: 'Siva' };

// Create a reducer function to handle name updates
const userReducer = (state: UserState, action: UserAction): UserState => {
  switch (action.type) {
    case 'UPDATE_NAME':
      return { ...state, name: action.payload };
    default:
      return state;
  }
};
```

### Step 2: Create the Context and Provider

```tsx
// Define the context type for the user
type UserContextType = {
  state: UserState;
  dispatch: React.Dispatch<UserAction>;
};

// Create the UserContext
const UserContext = createContext<UserContextType | undefined>(undefined);

// Custom hook to use the UserContext
const useUser = () => {
  const context = useContext(UserContext);
  if (!context) {
    throw new Error('useUser must be used within a UserProvider');
  }
  return context;
};

// Create the provider component
type UserProviderProps = {
  children: ReactNode;
};

export const UserProvider: React.FC<UserProviderProps> = ({ children }) => {
  const [state, dispatch] = useReducer(userReducer, initialState);

  return (
    <UserContext.Provider value={{ state, dispatch }}>
      {children}
    </UserContext.Provider>
  );
};
```

### Step 3: Use the Context in a Component

```tsx
import React from 'react';
import { useUser } from './UserContext';

const UserProfile: React.FC = () => {
  const { state, dispatch } = useUser();

  return (
    <div>
      <h1>Current Name: {state.name}</h1>
      <button onClick={() => dispatch({ type: 'UPDATE_NAME', payload: 'Sivamani' })}>
        Update Name to Sivamani
      </button>
    </div>
  );
};

export default UserProfile;
```

### Step 4: Wrap the Application with the Provider

```tsx
import React from 'react';
import ReactDOM from 'react-dom';
import { UserProvider } from './UserContext';
import UserProfile from './UserProfile';

const App: React.FC = () => {
  return (
    <UserProvider>
      <UserProfile />
    </UserProvider>
  );
};

ReactDOM.render(<App />, document.getElementById('root'));
```

### Key Points for Interviews:
- **useReducer**: Manages the state of the user’s name, allowing the name to be updated from "Siva" to "Sivamani".
- **useContext**: Shares the state and the dispatch function globally, so any component can access and modify the name.
- **Custom Hook**: The `useUser` hook is used to easily access the user context without needing to repeat `useContext(UserContext)` in every component.

