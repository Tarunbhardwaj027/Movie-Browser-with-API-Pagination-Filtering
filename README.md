# Movie-Browser-with-API-Pagination-Filtering

🛠️ Core Functionalities Overview
1. Fetching & Displaying Movie Data
Use fetch('https://api.tvmaze.com/shows') on page load.

Extract key attributes:

image.medium for poster

name for title

genres array (e.g., [Drama, Thriller])

rating.average

Store the full dataset locally to manage filtering/sorting without refetching.

2. Pagination Logic
Show 6 movies per page.

Track currentPage in:

URL query string (e.g., ?page=3) or

localStorage

Create “Previous” and “Next” buttons.

Slice the array:

const startIndex = (currentPage - 1) * 6;
const visibleMovies = allMovies.slice(startIndex, startIndex + 6);


3. Sorting Dropdown
Options:

Rating: High to Low → sort by rating.average

Title: A–Z → sort alphabetically by name

Combine sorting with the filtered dataset.

4. Filtering by Genre
Build a genre list dynamically from all movies.

Allow multiple genres or single-select dropdown.

Apply filtering before sorting and pagination:

const filtered = allMovies.filter(movie => movie.genres.includes(selectedGenre));


💄 Layout & Styling Suggestions
Responsive Grid (3x2)
Use CSS Grid or Tailwind’s grid-cols-3 gap-4 on medium/large screens.

Stack items vertically on small screens (grid-cols-1).

UI
Show page number

Provide feedback when no movies match filters

Optional loading spinner

🌟 Bonus Features
Watch Later
Add a bookmark icon/button.

Use localStorage:

js
const watchLater = JSON.parse(localStorage.getItem('watchLater')) || [];
localStorage.setItem('watchLater', JSON.stringify(updatedList));

Persisting UI State
Use URL params for page, genre, and sort.

On reload, read from window.location.search or localStorage to restore state.

        🤓 Tech Stack Summary
        
Feature	                Implementation
API Data	              fetch()
Pagination	            Array slicing
Sorting	                array.sort()
Filtering	              array.filter()
State Persistence	      URL params / localStorage
Styling	                Tailwind or CSS Grid
