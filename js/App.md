# Oprette en App klasse
For at håndtere instantiering af din webapp oprettes en App.js fil, der fungerer til at opsætte og loade hvad der skal bruges når appen starter op. Samtidig kan den køre en række funktioner når appen lukkes igen. På denn måe kommer din app også til at køre som en instans af en klasse.

## Opsætning af klassen
Din App.js fil kan have følgende opsætning hvor der laves en App constructor, der ved instantiering kalder og opretter den data og de elementer der skal laves ved start. Start er i dette tilfælde når document er færdig med at blive loaded ind i browseren.

```javascript
// Import needed files to start up the app
import FavoriteController from 'FavoriteController'

class App{
  constructor() {
    /** 
     * HEADER
    */
    // Create headerHTML
    const headerHTML = `
      <!-- HTML used for your header -->
    `
    // Insert headerHTML in document
    document.body.insertAdjacentHTML('beforeend', headerHTML)


    /** 
     * SEARCH SECTION
    */
    // Create new SearchControllerController and call setupview() method


    /** 
     * FAVORITE SECTION
    */
    // Create new FavoritesController and call setupview() method
    new FavoriteController().setupView();


    /**
     * FOOTER
    */
    // Create footerHTML
    // Insert footerHTML in document


    // Eventlistener that saves to localStorage when the window is unloaded.
    // window.addEventListener('beforeunload', (e) => store.saveToLocalStorage())
  }
}

// Start at new app instance when document content is loaded
document.addEventListener('DOMContentLoaded', (e) => new App())
```

Der er i eksemplet lavet opsætning til favorit sektionen og til at starte en ny instans. Du skal selv lave resten af opsætningen og importere filen i webpacks entry fil (index.js som standard). 