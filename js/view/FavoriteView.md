# Opsætning af FavoriteView
Fil til opsætning af hele din favorit sektion. Filen skal have to funktioner `createFavoriteView(store)` og `addMovieToView`. 

## Opsætning af createFavoriteView
Funktionen acceptere en parameter, som er vores store objekt. Så kaldes `MovieCardComponent().render() fra MovieCardComponent.js` for hvert object i `store`. Til sidst returneres HTML for hele favorit sektionen hvor hvert movieCard er placeret i.

## Opsætning af addMovieToView
Funktioen skal returnere HTML til et nyt movieCardComponent. Indsætning af denne HTML i index.html sker i FavoritController.js filen.  

## Eksempel på hvordan filen kan sættes op
```javascript
import MovieCardComponent from './MovieCardComponent'

export function createFavoriteView(store){
  let movieCardHTML = ''
  if (store) {
    store.movieDB.forEach(movieObject => {
      movieCardHTML += new MovieCardComponent(movieObject).render()
    })
  }

  return `
    <!-- Favorite Movies -->
    <div class="container">
      <h2>Favorite Movies</h2>
    </div>

    <main>       
      <section class="col">  
        <div class="grey darken-4" id="sec">
          <div class="container">
            <div class="row" id="favoriteSection">
              ${movieCardHTML}
            </div>
          </div>
        </div>
      </section>
  `
}

export function addMovieToView(movie){
  return movieCardHTML = new MovieCardComponent(movie).render()
}
```