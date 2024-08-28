Here's a simple example using React Router v6. This example demonstrates how to set up a basic routing system in a React application with multiple pages.

### **1. Install React Router**

First, you need to install `react-router-dom`:

```bash
npm install react-router-dom
```

### **2. Setting Up the Basic Structure**

We'll create a simple app with three pages: Home, About, and Contact.

### **3. Creating the Components**

Create simple components for Home, About, and Contact pages.

#### **3.1. Home Component**

```javascript
// Home.js

import React from 'react';

const Home = () => {
    return (
        <div>
            <h1>Home Page</h1>
            <p>Welcome to the Home Page</p>
        </div>
    );
};

export default Home;
```

#### **3.2. About Component**

```javascript
// About.js

import React from 'react';

const About = () => {
    return (
        <div>
            <h1>About Page</h1>
            <p>Learn more about us on this page.</p>
        </div>
    );
};

export default About;
```

#### **3.3. Contact Component**

```javascript
// Contact.js

import React from 'react';

const Contact = () => {
    return (
        <div>
            <h1>Contact Page</h1>
            <p>Get in touch with us through this page.</p>
        </div>
    );
};

export default Contact;
```

### **4. Setting Up the Routes**

Now, set up the routes in your `App.js` using `react-router-dom` v6.

```javascript
// App.js

import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './Home';
import About from './About';
import Contact from './Contact';

function App() {
    return (
        <Router>
            <nav>
                <ul>
                    <li>
                        <Link to="/">Home</Link>
                    </li>
                    <li>
                        <Link to="/about">About</Link>
                    </li>
                    <li>
                        <Link to="/contact">Contact</Link>
                    </li>
                </ul>
            </nav>

            <Routes>
                <Route path="/" element={<Home />} />
                <Route path="/about" element={<About />} />
                <Route path="/contact" element={<Contact />} />
            </Routes>
        </Router>
    );
}

export default App;
```

### **5. Explanation**

- **Router**: `BrowserRouter` is used to wrap the entire application, enabling the routing functionality.
- **Routes**: The `Routes` component replaces `Switch` in React Router v6. It contains all the `Route` components, defining which components should be rendered for each path.
- **Route**: Each `Route` has a `path` prop to define the URL and an `element` prop that specifies which component to render when that path is matched.
- **Link**: The `Link` component is used for navigation. It renders an anchor tag (`<a>`) but prevents the page from reloading when the link is clicked, allowing for a single-page application (SPA) behavior.

### **6. Running the Application**

If you're using `create-react-app` or a similar setup, you can run the application with:

```bash
npm start
```

### **7. Navigation Overview**

When you run this application:

- The `Home` component is displayed when you navigate to the root URL (`/`).
- The `About` component is displayed when you navigate to `/about`.
- The `Contact` component is displayed when you navigate to `/contact`.

The navigation links in the `nav` section allow you to switch between these routes without reloading the page.
