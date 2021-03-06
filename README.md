# PopularMovieMVP
Built an app, optimized for tablets, to help users discover popular and highly rated movies on the web. It displays a scrolling grid of movie trailers, launches a details screen whenever a particular movie is selected, allows users to save favorites, play trailers, and read user reviews. This app utilizes core Android user interface components and fetches movie information using themoviedb.org web API. MVP design pattern is implemented for the project architecture, and content provider is implemented for data persistence. 

<b>Note:</b> to use themoviedb API you need to update the class WebServiceProxy.java with you API key.

Here you can watch a screencast for the application, click on the image below:

[![Alt text for your video](https://cloud.githubusercontent.com/assets/1500868/12656770/91bf5828-c608-11e5-9f28-26c1e9664fe5.png)](https://www.youtube.com/watch?v=c6Ln5iDt2eo)

## User Interface - Layout
* Material design support library is used.
* Movies are displayed in the main layout via a grid of their corresponding movie poster thumbnails.
* UI contains a screen for displaying the details (movies details, video trailers and user rebiews) for a selected movie.
* UI contains an element (e.g., a spinner or settings menu) to toggle the sort order of the movies by: most popular, highest rated.
* UI contains a screen for displaying the details for a selected movie.
* Movie Details layout contains title, release date, movie poster, vote average, and plot synopsis.
* Movie Details layout contains a section for displaying trailer videos and user reviews.

## User Interface - Function
* When a user changes the sort criteria (most popular, highest rated, and favorites) the main view gets updated correctly.
* When a movie poster thumbnail is selected, the movie details screen is launched [Phone] or displayed in a fragment [Tablet].
* When a trailer is selected, app uses an Intent to launch the trailer.
* In the movies detail screen, a user can tap a button(for example, a star) to mark it as a Favorite.

## Network API Implementation
* In a background thread, app queries the /discover/movies API with the query parameter for the sort criteria specified in the settings menu. (Note: Each sorting criteria is a different API call.)
* App requests for related videos for a selected movie via the /movie/{id}/videos endpoint in a background thread and displays those details when the user selects a movie.
* App requests for user reviews for a selected movie via the /movie/{id}/reviews endpoint in a background thread and displays those details when the user selects a movie.

## Data Persistence
* App persists favorite movie details using a database
* App displays favorite movie details (texts, images and user reviews) even when offline
* App uses a ContentProvider* to populate favorite movie details

