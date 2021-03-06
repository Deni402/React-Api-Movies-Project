# React-Movies-API-Project
   ---
## Installation
   Clone or download the repo
   Run 'npm i' and 'npm run serve'

## Timeframe
  Two days

   ---

## Overview 
   As the title says, React-Movies-API-Project is a short team project of two days deadline where we had to create a website using an online free API which was a bit difficult to find but once we did, the fun and enjoying part started and we could play around with its potential by ReactJS as a front-end tool along with Sass, NodeJS, Bulma etc.
   
   As for my side of the project I had to create the routes for each path/component which had place in 'app.js', and then import react and axios in each new route so I can use 'componentDidMount' for taking my specific data like I did for 'singleMovie.js'. Styling was also one of my tasks and I used bulma for the majority and a bit of Sass to adjust the rest such as height, margins, paddings and background colors.
   
   ---
## Technologies used:
 Front end:
 HTML, SCSS, Bulma, React.js, Webpack, Babel 

   ---
## Main Page:

   The main page is divided into a navbar, hero with a searching bar which allows the user to access informations for any movie, and the first twenty trending movies.
   Our goal here was to keep the code and the design as clean as we could so we can focus more on the functionality and properties of ReactJS, and how can we use that to manipulate the specific part of the API that shows only the first twenty trending movies.

   ![Game Page - Win](https://i.imgur.com/fQk3GQ8.png)

## Navbar:  

![Game Page - Win](https://i.imgur.com/7Pg0uYu.png)

For the navbar we created a new component where we imported React and a link to the trending movies.  As I mentioned earlier, I used Bulma for most part of the design which in this case the navbar model had also a hamburger drop-down menu where I included the movie genres that unfortunetly we haven't got time to finish, but I'm looking forward to do so in the future features. 

       const Navbar = () => (
    <div className="navbar is-black is-bold">
    <div className="container">
      <div className="navbar-start">
        <Link className="navbar-item" to="/">Trending</Link>
      </div>
      <div className="navbar-item has-dropdown is-hoverable">
        <a className="navbar-link">
          Genres
        </a>
        <div className="navbar-dropdown">
          <a className="navbar-item">
            Action
          </a>
          <a className="navbar-item">
            Comedy
          </a>
          <a className="navbar-item">
            Crime
          </a>
          <a className="navbar-item">
            Horror
          </a>
          <a className="navbar-item">
            Thriller
          </a>
          <a className="navbar-item">
            War
          </a>
        </div>
      </div>
    </div>
 

## Hero & Searching bar: 

The process behind searching bar was to create a function with an event 'e' that returns the location of the event target value 'e.target.value', an input 'onChange' and a form 'onSubmit' that gives the user the specific movie. 
The hero was also a Bulma property easly inserted in our code.

         handleChange(e){
    if (e.target.value === '') location.reload()
    else { 
      this.setState({ search: e.target.value })
      console.log(this.state.search)
    }
  

    render() {
    console.log(this.state.movies.results)
    return (<div>
      <section className="hero is-light">
        <div className="hero-body">
          <div className="container">
            <form onSubmit={(e) => this.handleSubmit(e)}>
              <div className='column'>
                <input onChange={(e) => this.handleChange(e)} type='text' className='input is-large' placeholder='Search all Movies' />
              </div>
              <div className='column is-one-quarter'>
                <button type="submnit" value='submit'className='button is-link'>Search</button>
              </div>
            </form>
          </div>
        </div>
      </section>


## Trending movies: 

To get only the first twenty trending movies we had to create a 'class  Main' with a constructor and use the 'map' property through the results 'this.state.movies.results' inside of the 'render' function. 

              {this.state.movies.results.map((result, i) => {
                return <div key={i} className="column is-one-quarter-desktop is-one-third-tablet is-half-mobile">
                  <a href={`/main/${result.id}`}>
            
 The next step was creating another route for single movie 

     <Route path="/main/:id" component={SingleMovie} />

 then, when the user clicks on the movie's card, the APIs ID for the specific movie is called and the route is changing to single movie and returns more informations.

      componentDidMount(){
    const id = this.props.match.params.id
    axios.get(`https://api.themoviedb.org/3/movie/${id}?api_key=${process.env.API_Key}`)
      .then(res => this.setState({ movie: res.data }) )
      .catch(err => console.log(err))
    }

        render(){
    console.log(this.state.movie.genres[0].name)
    return (
      <div className='container'>
        <div className='card'>
          <div className='columns'>
            <div className='column is-one-third'>
              <img className='single' src={`https://image.tmdb.org/t/p/w500${this.state.movie.poster_path}`}/>
            </div>
            <div className='column, details'>
            
              <h1>{this.state.movie.title}</h1>
        
              <p>Vote avarage {this.state.movie.vote_average} </p>
           
              <p>{this.state.movie.overview}</p>
              <p>Relase date: {this.state.movie.release_date}</p>

              <p>Genre: {this.state.movie.genres[0].name}</p>
             
            </div>
          </div>
        </div>
      </div>

## Challenges & wins 

One of the challenges was finding a good algorithm that match us as a team for splitting the tasks and combine the code to get the final result, we decided that is important to finish the functionallity part first and crack it step by step on small tasks for each one. I was satisfyed with the process because I got to understand and enjoy every bit we made. 

## Key learnings
From this project I got to learn more about the functionality behind manipulating an External API using ReactJS, get used to the syntax of render, importing and exporting while creating new routes and components, why e.preventDefault() is so importand when it comes to reload a specific part of the page, improved my styling skills using Bulma and Sass, and also very important how to work in a team, understand and talk to my partners and split the tasks in a way that everyone understands the final code.

## Future features
  The next feature that we wanted to add was "Genres" dropdown of movies, placed on the top-right corner of the navbar which we never got to finish because of the short timeframe we had.
  In a future version of the site we would like to finish what we started and implement more features like "Add to favorites" button with a different route.