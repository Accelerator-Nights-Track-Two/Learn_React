Lesson 3: Creating Reusable Components with Props

Objective: The purpose of this lesson is to introduce props in React and demonstrate how to create reusable components. By the end of this lesson, you will understand how to abstract functionality into components and pass data to them using props. This builds on JavaScript fundamentals like function parameters and arguments, helping you see how they relate to React development.

Props (short for "properties") allow components to receive data from their parent components. This makes components dynamic and reusable, reducing code duplication.

Exercise:

Create a components folder and add a MovieCard component.
Refactor App.jsx to use the new MovieCard component.
Use props to pass movie details (title, image, and description) from App.jsx to MovieCard.
Build a MovieList component to map through the movies array and render a MovieCard for each movie.
Step-by-Step Guide:

1. Create the MovieCard Component
Inside a new components folder, create a file named MovieCard.jsx. This component will represent a single movie.

jsx
```
function MovieCard({ title, image, description }) {
  return (
    <div className="movie-card">
      <h2>{title}</h2>
      <img src={image} alt={title} />
      <p>{description}</p>
    </div>
  );
}


export default MovieCard;
```

Key Concepts:
The MovieCard component accepts props as its parameter.
Props are destructured in the function signature ({ title, image, description }) for easier access.
2. Refactor App.jsx
Import MovieCard into App.jsx and use it to render each movie.

jsx
```
import React, { useState } from 'react';
import MovieCard from './components/MovieCard';

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

function App() {
  const [movies, setMovies] = useState(initialMovies);

  return (
    <div>
      <h1>Movie App</h1>
      <div className="movie-list">
        {movies.map((movie) => (
          <MovieCard
            key={movie.id}
            title={movie.title}
            image={movie.image}
            description={movie.description}
          />
        ))}
      </div>
    </div>
  );
}

export default App;
```

Key Concepts:
Each MovieCard receives data as props (title, image, and description) from App.jsx.
The key prop helps React efficiently update and render components.
3. Create the MovieList Component
To further organize the code, create a MovieList.jsx component. This component will handle the mapping logic and render all MovieCard components.

MovieList.jsx
jsx
```
import MovieCard from './MovieCard';

function MovieList({ movies }) {
  return (
    <div className="movie-list">
      {movies.map((movie) => (
        <MovieCard
          key={movie.id}
          title={movie.title}
          image={movie.image}
          description={movie.description}
        />
      ))}
    </div>
  );
}

export default MovieList;
```
Refactor App.jsx
Now, use MovieList in App.jsx:

jsx
```
import React, { useState } from 'react';
import MovieList from './components/MovieList';

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

function App() {
  const [movies, setMovies] = useState(initialMovies);

  return (
    <div>
      <h1>Movie App</h1>
      <MovieList movies={movies} />
    </div>
  );
}

export default App;
```
Key Concepts:
The MovieList component receives the entire movies array as a prop.
This organizes the code into smaller, reusable components, improving maintainability.
Example Implementation:

Your application now has the following structure:

MovieCard.jsx - A reusable component to display individual movie details.
MovieList.jsx - A component that maps through the movies array and renders MovieCard components.
App.jsx - The parent component that manages state and renders the MovieList component.
When you load your app, the output will remain visually the same, but your code is now better organized and easier to extend.

Why Props Matter:

Props in React work like function parameters in JavaScript. They allow parent components to pass data to child components, making it possible to create dynamic and reusable components. By leveraging props, we avoid hardcoding data in components, making them more flexible and maintainable.

This setup prepares you for the next lesson, where you will learn about forms and state management to filter and search movies.