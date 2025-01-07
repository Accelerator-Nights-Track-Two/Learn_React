Lesson 1: Introduction to React and Setting Up Your Project

Objective:
The goal of this lesson is to introduce you to React, explain how it works conceptually, and guide you through setting up your first React project using Vite. By the end of this lesson, you will understand the relationship between the key files in a React application—index.html, main.jsx, and App.jsx—and how they work together using the DOM and Virtual DOM.

React is a JavaScript library for building user interfaces. Unlike traditional JavaScript applications that directly manipulate the DOM (Document Object Model), React introduces the concept of a Virtual DOM. This makes updates efficient by minimizing direct DOM manipulations, which can be slow and error-prone.

Exercise:

Set up a new React project using Vite.

Examine and understand the purpose of the key files: index.html, main.jsx, and App.jsx.

Write a simple component in App.jsx to render a welcome message.

Step-by-Step Guide:

1. Set Up Your React Project

To start, we’ll use Vite, a fast build tool for modern JavaScript applications.

Install Vite

Run the following commands:

```
    # Create a new Vite project
    npm create vite@latest react-movies-guide --template react

    # Navigate to your project directory
    cd react-movies-guide

    # Install dependencies
    npm install

    # Start the development server
    npm run dev
```

Vite will spin up a development server and provide a local URL for you to access your app.

2. Key Files in Your React Project

Let’s break down the important files:

index.html

Located in the public directory.

The only HTML file in your project.

Contains a single <div> with the id="root". React uses this as the mounting point for your entire application.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>React Movies Guide</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>
```

main.jsx

This file is the entry point of your application.

Imports React and ReactDOM (for rendering the app into the DOM).

Links your App component to the root div in index.html.

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

Key Concepts: ReactDOM’s createRoot tells React where to render your application. Here, we specify the root element from index.html.

App.jsx

This is the root component of your application. All other components will eventually be included in or referenced from this file.

```javascript
function App() {
  return (
    <div>
      <h1>Welcome to the React Movies Guide!</h1>
      <p>Let's learn React by building a movie app.</p>
    </div>
  );
}

export default App;
```

Key Concepts: A React component is simply a JavaScript function that returns JSX. JSX (JavaScript XML) is a syntax extension for JavaScript that allows you to write HTML-like code inside your JavaScript.

3. React and the Virtual DOM

React uses a Virtual DOM, which is an in-memory representation of the actual DOM. When a component’s state or props change:

React updates the Virtual DOM.

It compares the new Virtual DOM with the previous one (a process called "diffing").

React updates only the parts of the real DOM that changed, making updates fast and efficient.

Example Implementation:

By now, your project should have the following:

index.html provides the root element.

main.jsx renders the App component inside the root element.

App.jsx contains the initial structure of your application.

When you start your development server with npm run dev, you should see a page displaying:

Welcome to the React Movies Guide!
Let's learn React by building a movie app.

This setup prepares you for the next lesson, where we will introduce state and begin building the movie app interface.