# Oprette FavoriteController
Funktioner til opsætning af favorit sektionen med event listeners. Dette gøres ved at kalde favorit view for at lave HTML delen og efterfølgende opsætte en event listener på favorit sektionen der finder ud af 

Sørger for at lave instanser af favorit sektionen. Sætter HTML op til favoritsektionen, laver en ny instanst af FavoritView og kalder `populateWithMovies()` der genererer HTML for alle movie cards.

## Opsætning af funktioner
Filen skal importere createFavoriteView fra FavoritView for at lave en ny favoritView. Opret funktionen setupFavorite() der kalder createFavoriteView med store som parameter. Opsæt herefter en eventlistener på sektionen, som lytter efter `click` og ved et event fjerner det card som er parrent til klikket.

## Eksempel på FavoritController.js
Hvis du har behov for hjælp til hvordan du kan opsætte filen, kan du se på eksemplet her under. Det er ikke et krav at den er sat op præcis sådan. 

```javascript 
import { store } from '../model/Store-OLD';
import { createFavoriteView, addMovieToView } from '../view/FavoriteView'

export function setupFavorite(){
  // Setup view and append to document
  const favoriteHTML = createFavoriteView(store)
  document.body.insertAdjacentHTML('beforeend', favoriteHTML)
  
  const favoriteSection = document.getElementById('favoriteSection')
  // Setup eventlisteners
  favoriteSection.addEventListener('click', (event) => {
    const clickedElement = event.target
    if (clickedElement.matches('a.favorite-movie-button')) {
      console.log(clickedElement.dataset)
      // Can also use clickedElement.dataset
      // Performance:
      // https://jsperf.com/data-dataset
      const movieID = clickedElement.getAttribute('data-id')
      clickedElement.closest('article').remove()
      console.log(`Removed movie with imdbID ${movieID} from favorite section`)
    }
  })
}
```

