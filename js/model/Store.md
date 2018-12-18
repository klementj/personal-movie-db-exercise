# Oprette en single store
Formål at håndtere et objekt til data, som din app kan læse og skrive til. Uanset hvilket modul der skriver eller læser data, så sker det fra det samme objekt. Store skal også kunne gemme og hente data til og fra browserens [localStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage).

## Opsætning af constructor
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

## Gemme og hente fra browserens localStorage
For at give brugeren af din app en god oplevelse og gemme deres data, fx hvis browseren lukkes eller computeren genstartes, skal du gemmme `movieDB` i browserens localStorage. I eksemplet med metoden `saveToLocalStorage()` laver du et JavaScript Objekt om til en streng. Når du loader denne streng igen og laver den om med `JSON.parse()` skal du være opmærksom på, at den ikke bliver lavet om til et JavaScript Objekt men et JSON Objekt. Du skal derfor huske at bruge din `Movie` klasse til at lave hvert JSON Objekt om til et JavaScript Objekt.

For at læse mere om forskellene mellem de to kan du læse denne artikel [JavaScript Object vs JSON](https://medium.com/techtrument/javascript-object-vs-json-117965ea3dea)

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
