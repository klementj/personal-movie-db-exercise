# Oprette MovieCardComponent.js
Denne fil skal kunne fungere som et genbrugeligt komponent i din webapp. Så alle de steder hvor der skal oprettes et movie card kan du importere dette modul, instantiere klassen med de rigtige properties og få returneret et stykke HTML som udgør en film.

## Opsætning af klassen
Lav en constructor til din klasse, der modtager et movie objekt. Lav også en metoder der består af HTML til et enkelt movie card og sæt filmenes variabler ind hvor de skal være. Brug [template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) til det. Du kan fx kalde metoden for `render()` eller `createCard()`.

## Eksempel på opsætning
```javascript
export default class MovieCardComponent{
  constructor(movie){
    this.title = movie.Title
    this.poster = movie.Poster
    this.plot = movie.Plot
    this.year = movie.Year
    this.genre = movie.Genre
    this.id = movie.imdbID  
  }

  render(){
    return `
      <article class="col s12 m5 l3">
        <div class="card">
          <div class="card-image waves-effect waves-block waves-light">
            <img class="activator" src="${this.poster}">
          </div>
          <div class="card-content">
            <span class="card-title activator white-text text-darken-4">${this.title}<i class="material-icons right">arrow_upward</i></span>
            <p>Year: ${this.year}<br>Genre: ${this.genre}</p>
            <p><a href="#" class="favorite-movie-button">${ this.fav === true ? `remove from fav` : `add to fav` }Add to Favorites</a></p>
          </div>
          <div class="card-reveal black">
            <span class="card-title white-text text-darken-4">${this.title}<i class="material-icons right">close</i></span>
            <p>${this.plot}</p>
          </div>
        </div>
    </article>
    `
  }
}
```

## Tilføje et ID til hvert card
Du har måske lagt mærke til at der i min constructor er tilføjet et ID. Dette bliver tilføjet til hvert movie card som en [custom-data-attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/data-*). Tilføj en data- attribut til cardets knap så det ser ud som i mit eksempel. Jeg har givet min data attribut et navn som data-id.

```javascript
...
  <p><a type="button" class="favorite-movie-button" data-id="${this.id}">...</a></p>
...
```