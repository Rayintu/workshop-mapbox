# Mapbox in ASP.NET React

## prerequisites
* .NET 3.1 preview
* Node
* React

Omdat er gewerkt wordt met React wordt het aanbevolen om met visual studio code of een andere webdevelopment gerichte IDE te gebruiken. Visual studio gaat niet zo goed om met React. Binnen visual studio kan er gebruik gemaakt worden van een knop om de code te builden en uit te voeren maar in deze workshop wordt er gebruik gemaakt van de commandline.

## Stap 1 Project setup

Kies een locatie voor dit project en kopieer het pad. Open een command line interface, navigeer naar de gewenste locatie en voer het volgende commando uit:
```
dotnet new react -o map-box-workshop
```
Vervolgens wordt de library die we gebruiken geïnstalleerd. In deze workshop wordt de library react-map-gl gebruikt. Deze library is ontwikkeld door Uber. Navigeer naar de map binnen het project genaamd: 'ClientApp' 
Als je dezelfde naam als hierboven gebruikt hebt voor jouw project kan dat met het volgende commando:
```
cd map-box-workshop/ClientApp
```
en voer het volgende commando uit:
```
npm install --save react-map-gl
```
ga vervolgens terug naar de hoofdmap
```
cd ../
```
En voer het volgende commando uit:
```
dotnet build
```
De eerste keer dat dit uitgevoerd wordt, word ook npm install uitgevoerd. Dit duurt heel erg lang dus ondertussen kunnen er alvast een aantal dingen geregeld worden. 

In deze repo staan de volgende twee bestanden: airbnblocations.json en map-marker.png. Maak binnen de source map van de ClientApp de mappen 'geoData' en 'images' aan. Download de bestanden en plaats ze in deze mappen. 

Vervolgens heb je ook nog een een mapbox accestoken nodig. Zonder deze token krijg je het volgende te zien op je scherm wanneer je mapbox implementeert: 
<img src="workshopImages/noTokenWarning.png">
Om de token te krijgen moet je een account maken op https://www.mapbox.com/. Wanneer je een account aangemaakt hebt en navigeert naar je profiel staat er een kopje 'Token' hier kun je jouw token vandaan halen. 

Hopelijk is de npm install nu klaar. Anders kun je jezelf even vermaken met dit: https://www.youtube.com/watch?v=PLOPygVcaVE

Wanneer dit uiteindelijk klaar is voer het volgende commando uit:
```
dotnet run
```

Als het goed is wordt nu de volgende pagina geopend:
