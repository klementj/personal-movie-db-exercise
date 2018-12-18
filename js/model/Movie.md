# Oprette en Movie.js model
Filen består af en klasse du skal bruge til, at oprette movie objekter i din app. Formålet er at du kan få data ind som fx har anden navngivning på properties, end dem du bruger i din app. Fx kan en tjeneste give dig en film plot i en property kaldet description. Måske leverer en tjeneste slet ikke denne property og derfor skal du kunne kontrollere hvad der så sker når du opretter dit movie objekt, så du senere i din app har styr på hvordan dine data objekter ser ud.

## Opsætning af klassen
Klassen består af en `constructor()` der modtager en film af typen objekt, og kan se ud som følgende:

```javascript
export default class Movie{
  constructor(movie){
    this.title = movie.Title
    this.year = movie.Year
    this.id = movie.imdbID
    this.poster = movie.Poster
    this.genre = movie.Genre
    this.plot = movie.Plot
  }
}
```

