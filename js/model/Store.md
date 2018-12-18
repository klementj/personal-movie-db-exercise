# Oprette en single store
Formål at håndtere et objekt til data, som din app kan læse og skrive til. Uanset hvilket modul der skriver eller læser data, så sker det fra det samme objekt. Store skal også kunne gemme og hente data til og fra browserens [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage).

## Opsætning af contructor
Opret klassen `Store` der i sin `constructor()` tjekker om der ligger data i localStorage, henter den ud og sætter data til en variabel. Hvis der ikke ligger noget data i localStorage så returner et tomt objekt og log en fejl i konsollen.

## Opsætning af metoder
Opret metoder som du kan bruge `store` instancen. Metoderne skal bruge til at hente og skrive film til objektet. Opret også private metoder som `Store` selv bruger til at gemme og læse fra localStorage.

Eksempel på en privat metode der tager et JavaScript Objekt, laver det til en streng og gemmer denne i localStoraga. Der er på forhånd oprettet et objekt i construktoren kaldet `movieDB`. 

```javascript
saveToLocalStorage(){
  localStorage['movieDB'] = JSON.stringify(movieDB)
}
```

Læse mere om hvordan du bruger [JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON) til at [konvertere en JavaScript værdi til en JSON string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) og [konvertere en JSON string tilbage til en JavaScript værdi](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

## Eksporter én enkelt instans
For at sikre at det er den samme instant, det samme objekt, du bruger på tværs af dine moduler og dermed på tværs af din app er det ikke klassen som eksporteres men i stedet en instans af klassen som eksporteres. Det kan fx gøres sådan her:

```javascript
export let store = new Store()
```

## Eksempel på Store.js
Nedenfor kan du se et eksempel på hvordan filens struktur kan se ud. Du skal selv lave den nødvendige kode for at få `constructor()` og metoder til at virke.

```javascript
class Store{

  

  constructor(){
    let movieDB

    if (!localStorage.getItem('movieDB')) {
      // Set and return movieDB with movies data
      console.log('Movies test data setup: ', movieDB)
    } else {
      // Set and return movies data, loaded from LocalStorage
      console.log('MovieDB loaded from localsStorage: ', movieDB)
    }
  }

  addToStore(movie){
    // Add a movie object to the movieDB object
  }

  removeFromStore(movieId){
    // Remove a movie object from the movieDB object
  }

  saveToLocalStorage(){
    // Save movieDB object to localStorage
  }

  loadFromLocalStorage(){
    // Load movieDB object from localStorage
  }

}

export let store = new Store();
```
