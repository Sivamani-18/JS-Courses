[Back to main](README.md#more-topic)

## Why Redux Toolkit?

Redux Toolkit addresses many pain points of traditional Redux:

- **Less boilerplate:** `createSlice` lets you define the initial state, reducers, and actions all in one place.
- **Built-in Thunks:** `createAsyncThunk` provides a streamlined way to handle async operations like API calls.
- **Immutability and Immer:** Redux Toolkit uses Immer under the hood, allowing us to write "mutative" logic in reducers that is safely converted to immutable updates.

## Getting Started

Before we dive into code, make sure you have Redux Toolkit installed:

```bash
npm install @reduxjs/toolkit react-redux
```

## Example: Fetching Data with `createAsyncThunk` and `createSlice`

In this example, we'll create a simple slice of state that handles fetching data from an API. We'll use `createAsyncThunk` to handle the asynchronous data fetching and `createSlice` to manage the state and reducers.

### Step 1: Setting Up `createSlice` and `createAsyncThunk`

Let's create a new slice to manage a list of posts:

```js
// src/features/posts/postsSlice.js
import { createSlice, createAsyncThunk } from "@reduxjs/toolkit";

// Step 1: Create an async thunk for fetching posts
export const fetchPosts = createAsyncThunk(
  "posts/fetchPosts",
  async (_, thunkAPI) => {
    try {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts");
      const data = await response.json();
      return data;
    } catch (error) {
      return thunkAPI.rejectWithValue({ error: error.message });
    }
  }
);

// Step 2: Create a slice
const postsSlice = createSlice({
  name: "posts",
  initialState: {
    posts: [],
    status: "idle", // 'idle' | 'loading' | 'succeeded' | 'failed'
    error: null,
  },
  reducers: {
    // You can define synchronous reducers here if needed
  },
  extraReducers: (builder) => {
    builder
      .addCase(fetchPosts.pending, (state) => {
        state.status = "loading";
      })
      .addCase(fetchPosts.fulfilled, (state, action) => {
        state.status = "succeeded";
        state.posts = action.payload;
      })
      .addCase(fetchPosts.rejected, (state, action) => {
        state.status = "failed";
        state.error = action.payload.error;
      });
  },
});

export default postsSlice.reducer;
```

### Step 2: Setting Up the Redux Store

Now that we have our slice, let's set up the Redux store and add the `posts` reducer:

```js
// src/app/store.js
import { configureStore } from "@reduxjs/toolkit";
import postsReducer from "../features/posts/postsSlice";

export const store = configureStore({
  reducer: {
    posts: postsReducer,
  },
});
```

### Step 3: Using the Slice in a Component

Now, let's use this slice in a component to fetch and display the posts:

```js
// src/components/PostsList.js
import React, { useEffect } from "react";
import { useSelector, useDispatch } from "react-redux";
import { fetchPosts } from "../features/posts/postsSlice";

const PostsList = () => {
  const dispatch = useDispatch();
  const posts = useSelector((state) => state.posts.posts);
  const status = useSelector((state) => state.posts.status);
  const error = useSelector((state) => state.posts.error);

  useEffect(() => {
    if (status === "idle") {
      dispatch(fetchPosts());
    }
  }, [status, dispatch]);

  if (status === "loading") {
    return <div>Loading...</div>;
  }

  if (status === "failed") {
    return <div>Error: {error}</div>;
  }

  return (
    <div>
      <h2>Posts</h2>
      {posts.map((post) => (
        <div key={post.id}>
          <h3>{post.title}</h3>
          <p>{post.body}</p>
        </div>
      ))}
    </div>
  );
};

export default PostsList;
```

### Step 4: Integrating the Component in Your App

Finally, wrap your main component with `Provider` to connect the Redux store:

```js
// src/App.js
import React from "react";
import { Provider } from "react-redux";
import { store } from "./app/store";
import PostsList from "./components/PostsList";

function App() {
  return (
    <Provider store={store}>
      <div className="App">
        <PostsList />
      </div>
    </Provider>
  );
}

export default App;
```

### Recap

In this example, we covered the following:

- Using `createAsyncThunk` to handle asynchronous actions like API calls.
- Using `createSlice` to define a slice of state, reducers, and actions.
- Setting up a Redux store using `configureStore`.
- Connecting Redux state to a React component using `useSelector` and `useDispatch`.

Redux Toolkit makes it simpler to write Redux logic, reducing boilerplate and adding helpful utilities. With `createAsyncThunk`, we can easily manage complex async workflows, while `createSlice` allows us to define reducers and actions in one place.

### Conclusion

Redux Toolkit significantly simplifies state management in React applications. By using `createSlice` and `createAsyncThunk`, you can handle both synchronous and asynchronous state updates in a more manageable way. Whether you're a beginner or an experienced developer, Redux Toolkit's streamlined API helps you build scalable and maintainable applications.
