Lesson 6: Implementing Routing with React Router

Objective:
The goal of this lesson is to introduce React Router and demonstrate how to add navigation between multiple pages in a React app. By the end of this lesson, students will be able to set up routes, navigate between pages, and pass data through route parameters. This builds on React components and state management, showing how a single-page application (SPA) can mimic the behavior of a multi-page website.

Exercise:

Install React Router and set up routing for the app.

Create two new pages: MovieDetails and Favorites.

Implement navigation between the Home page, Movie Details page, and Favorites page.

Step-by-Step Guide:

1. Install React Router

First, install React Router in your project:

```
npm install react-router-dom
```

2. Set Up a Basic Router

Wrap the application in a BrowserRouter component in index.jsx to enable routing.

```
import React from 'react';
import ReactDOM from 'react-dom';
import { BrowserRouter } from 'react-router-dom';
import App from './App';

ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  document.getElementById('root')
);
```

3. Define Routes in App.jsx

Use the Routes and Route components from React Router to define paths for your app.

```
import React, { useState } from 'react';
import { Routes, Route, Link } from 'react-router-dom';
import MovieDetails from './MovieDetails';
import Favorites from './Favorites';

function App() {
  const [movies, setMovies] = useState([
    { id: 1, title: 'Inception', description: 'A dream within a dream.', image: 'https://via.placeholder.com/150' },
    { id: 2, title: 'The Matrix', description: 'A simulated reality.', image: 'https://via.placeholder.com/150' },
  ]);

  const [favorites, setFavorites] = useState([]);

  return (
    <div>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/favorites">Favorites</Link>
      </nav>

      <Routes>
        <Route
          path="/"
          element={
            <div>
              <h1>Movie List</h1>
              {movies.map((movie) => (
                <div key={movie.id}>
                  <h2>{movie.title}</h2>
                  <img src={movie.image} alt={movie.title} />
                  <p>{movie.description}</p>
                  <Link to={`/movies/${movie.id}`}>Details</Link>
                </div>
              ))}
            </div>
          }
        />
        <Route path="/movies/:id" element={<MovieDetails movies={movies} />} />
        <Route path="/favorites" element={<Favorites favorites={favorites} />} />
      </Routes>
    </div>
  );
}

export default App;
```

4. Create the MovieDetails Component

This component displays details for a single movie. Use the useParams hook to get the movie ID from the route.

```
import React from 'react';
import { useParams } from 'react-router-dom';

function MovieDetails({ movies }) {
  const { id } = useParams();
  const movie = movies.find((m) => m.id === parseInt(id));

  if (!movie) return <div>Movie not found!</div>;

  return (
    <div>
      <h1>{movie.title}</h1>
      <img src={movie.image} alt={movie.title} />
      <p>{movie.description}</p>
    </div>
  );
}

export default MovieDetails;
```

5. Create the Favorites Component

This component displays the list of favorite movies. You can allow users to add movies to favorites by passing a function as a prop.

```
import React from 'react';

function Favorites({ favorites }) {
  if (favorites.length === 0) return <div>No favorites yet!</div>;

  return (
    <div>
      <h1>Your Favorites</h1>
      {favorites.map((movie) => (
        <div key={movie.id}>
          <h2>{movie.title}</h2>
          <img src={movie.image} alt={movie.title} />
        </div>
      ))}
    </div>
  );
}

export default Favorites;
```

Example Implementation:

The home page (/) lists all movies and provides a link to each movie's details.

The movie details page (/movies/:id) displays detailed information about the selected movie.

The favorites page (/favorites) displays movies the user has marked as favorites.

Next Steps:
This lesson introduces routing and navigation in React. In the next lesson, you can explore advanced topics like protected routes, lazy loading, and enhancing the user experience with animations or route transitions.