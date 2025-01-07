Lesson 4: React Forms and State Management

Objective:
The purpose of this lesson is to introduce React forms and demonstrate how to manage input fields using state. By the end of this lesson, you will understand how to handle user input in React, update state based on form interactions, and filter a list of movies dynamically. This builds on JavaScript fundamentals like event handling and string/array manipulation.

Forms in React are used to collect input from users. Controlled components, which tie the value of a form element to React state, are a key concept in managing form data effectively.

Exercise:

Add a search bar to App.jsx.

Use React state to manage the input value of the search bar.

Filter the movie list based on the search term.

Step-by-Step Guide:

1. Add a Search Bar to App.jsx

Create a simple search bar element in the App.jsx file. Add a form input element above the movie list.

```
import React, { useState } from 'react';

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
  const [searchTerm, setSearchTerm] = useState('');

  const handleSearchChange = (event) => {
    setSearchTerm(event.target.value);
  };

  const filteredMovies = movies.filter((movie) =>
    movie.title.toLowerCase().includes(searchTerm.toLowerCase())
  );

  return (
    <div>
      <h1>Movie App</h1>
      <input
        type="text"
        placeholder="Search movies..."
        value={searchTerm}
        onChange={handleSearchChange}
      />
      <div className="movie-list">
        {filteredMovies.map((movie) => (
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

2. Manage Input with React State

Create a searchTerm state using the useState hook.

Update the searchTerm state whenever the user types into the input field by adding an onChange event handler to the input.

3. Filter Movies Dynamically

Use the filter method on the movies array to create a new array (filteredMovies) that contains only the movies whose titles match the searchTerm.

Convert both the searchTerm and movie titles to lowercase for case-insensitive filtering.

Map over the filteredMovies array to render only the matching movies.

Example Implementation:

The application now allows users to type into the search bar and instantly filters the displayed movies based on the input. For example:

Initially, all movies (Inception and The Matrix) are displayed.

If the user types "Matrix," only The Matrix is shown.

If the user types "xyz," no movies are displayed.

Next Steps:
This lesson introduces state management for form inputs and real-time filtering. In the next lesson, we will replace the static movie data with an API call and explore data fetching in React.