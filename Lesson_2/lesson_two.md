Lesson 2: Building the Movie App with Static Data

Objective:
The purpose of this lesson is to introduce React state and demonstrate how to build the initial structure of the movie app using static data. By the end of this lesson, you will understand how to manage state in React and structure your application to display movie data dynamically.

State is an essential concept in React. It allows components to "remember" information and re-render when that information changes. For this lesson, we will use static data to simulate a database and learn how to display it on the page.

Exercise:

Define a static array of two movies in App.jsx.

Use React state to store the movie data.

Build the structure of the front end by rendering each movie as a card.

Step-by-Step Guide:

1. Define Static Movie Data

In App.jsx, create a static array of movies. Each movie should have a title, image URL, and description.

```
const initialMovies = [
  {
    id: 1,
    title: 'Inception',
    image: 'https://via.placeholder.com/150',
    description: 'A thief who steals corporate secrets through the use of dream-sharing technology.',
  },
  {
    id: 2,
    title: 'The Matrix',
    image: 'https://via.placeholder.com/150',
    description: 'A computer hacker learns about the true nature of his reality and his role in the war against its controllers.',
  },
];
```

2. Use React State

Use the useState hook to store the movie data.

```
import React, { useState } from 'react';

function App() {
  const [movies, setMovies] = useState(initialMovies);

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

3. Build the Movie Card Structure

For now, we are directly mapping over the movies array to display each movie. Each movie is represented as a "card" with a title, image, and description. This structure will be refactored into a reusable component in the next lesson.

Example Implementation:

Your application should now display the two movies from the static array. The page should look something like this:

Movie App

```
- Inception
  [Image]
  A thief who steals corporate secrets through the use of dream-sharing technology.

- The Matrix
  [Image]
  A computer hacker learns about the true nature of his reality and his role in the war against its controllers.
```

This setup prepares you for the next lesson, where we will refactor the code to introduce reusable components and props.