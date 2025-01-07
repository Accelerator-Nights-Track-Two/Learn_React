Lesson 5: Fetching Data with useState

Objective:
The goal of this lesson is to introduce data fetching in React using the useState and useEffect hooks. By the end of this lesson, you will understand how to fetch movie data from an external API, manage asynchronous state, and handle potential quirks like dependency arrays and side effects.

This lesson builds on the concept of state management from earlier lessons and introduces lifecycle behaviors through useEffect, helping students understand how React interacts with external data sources.

Exercise:

Replace the static movie data with an API call.

Fetch movie data when the app loads using useEffect.

Handle loading and error states gracefully.

Step-by-Step Guide:

1. Set Up an API Call

Replace the static initialMovies array in App.jsx with a real API call. For this example, we will use the OMDB API or any mock API providing movie data. You'll need an API key to access OMDB, or you can use a service like jsonplaceholder.typicode.com for practice.

Install Axios or use the Fetch API to make HTTP requests.

```
npm install axios
```

2. Fetch Data with useEffect

Update the App.jsx file to fetch movie data when the app loads.

```
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function App() {
  const [movies, setMovies] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchMovies = async () => {
      try {
        const response = await axios.get('https://api.example.com/movies');
        setMovies(response.data);
        setLoading(false);
      } catch (err) {
        setError('Failed to fetch movies');
        setLoading(false);
      }
    };

    fetchMovies();
  }, []); // Empty dependency array ensures this runs only once on component mount

  if (loading) return <div>Loading...</div>;
  if (error) return <div>{error}</div>;

  return (
    <div>
      <h1>Movie App</h1>
      <div className="movie-list">
        {movies.map((movie) => (
          <div key={movie.id} className="movie-card">
            <h2>{movie.title}</h2>
            <img src={movie.image} alt={movie.title} />
            <p>{movie.description}</p>
          </div>
        ))}
      </div>
    </div>
  );
}

export default App;
```

3. Understand useEffect

When it runs: The useEffect hook with an empty dependency array ([]) runs only once after the component mounts.

Dependency array: Add variables to the dependency array to trigger the effect whenever those variables change.

Cleanup: If necessary, return a cleanup function to run when the component unmounts or dependencies change.

4. Handle Loading and Error States

Use loading state to display a loading message until the data is fetched.

Use error state to display an error message if the fetch fails.

Example Implementation:

Initially, the app displays a "Loading..." message.

Once the API call completes, it shows the fetched movies.

If the API call fails, it displays an error message like "Failed to fetch movies."

Next Steps:
This lesson introduces asynchronous state management and lifecycle behaviors in React. In the next lesson, we will enhance the app with routing to navigate between different pages, such as movie details and a favorites list.