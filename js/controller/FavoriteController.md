# Oprette FavoriteController
Sørger for at lave instanser af favorit sektionen. Sætter HTML op til favoritsektionen, laver en ny instanst af FavoritView og kalder `populateWithMovies()` der genererer HTML for alle movie cards.

## Opsætning af klassen
Klassen skal, som du allerede har gættet, importere FavoritView for at kunne lave en ny instans og kalde metoden. FavoritController skal endnu ikke have en `constructor()`. Opsæt en metode kaldet `setupView()` der laver alle movie cards, sætter denne data ind i HTML strukturen for resten af sektionen og indsætter denne samlede HTML struktur for favorit sektionen ind i index.html filens body.

## Eksempel på FavoritController.js
Hvis du har behov for hjælp til hvordan du kan opsætte filen, kan du se på eksemplet her under. Det er ikke et krav at den er sat op præcis sådan.

```javascript 
import FavoriteView from '../view/FavoriteView'

export default class FavoriteController{

  setupView(){
    let movieCardHTML = new FavoriteView().populateWithMovies()
    
    const favoritHTML = `
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

    document.body.insertAdjacentHTML('beforeend', favoritHTML)
  }
}
```

