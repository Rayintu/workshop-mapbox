# Mapbox in ASP.NET React

## prerequisites
* .NET 3.1 preview
* Node
* React

Omdat er gewerkt wordt met React wordt het aanbevolen om met visual studio code of een andere webdevelopment gerichte IDE te werken. Visual studio gaat niet zo goed om met React. Binnen visual studio kan er gebruik gemaakt worden van een knop om de code te builden en uit te voeren maar in deze workshop wordt er gebruik gemaakt van de commandline.

## Stap 1 Project setup

Kies een locatie voor dit project en kopieer het pad. Open een command line interface, navigeer naar de gewenste locatie en voer het volgende commando uit om volgens het ASP.NET react template een project te maken:
```
dotnet new react -o map-box-workshop
```
Vervolgens wordt de library die we gebruiken geïnstalleerd. In deze workshop wordt de library react-map-gl gebruikt als react wrapper voor mapbox gl js. Deze library is ontwikkeld door Uber. Navigeer naar de map binnen het project genaamd: 'ClientApp' 
Als je dezelfde naam als hierboven gebruikt hebt voor jouw project kan dat met het volgende commando:
```
cd map-box-workshop/ClientApp
```
Voer hierna het volgende commando uit:
```
npm install --save react-map-gl
```

Wanneer dit uitgevoerd wordt, worden alle andere npm packages ook geïnstalleerd. Dit duurt heel erg lang dus ondertussen kunnen er alvast een aantal andere dingen geregeld worden. 

In deze repo staan de volgende twee bestanden: airbnblocations.json en map-marker.png. Maak binnen de source map van de ClientApp de mappen 'geoData' en 'images' aan. Download de bestanden en plaats ze in deze mappen. 

Vervolgens heb je ook nog een een mapbox accestoken nodig. Zonder deze token krijg je het volgende te zien op je scherm wanneer je mapbox implementeert: 

<img src="workshopImages/noTokenWarning.png">
Om de token te krijgen moet je een account maken op https://www.mapbox.com/  Wanneer je een account aangemaakt hebt en navigeert naar je profiel staat er een kopje 'Token' hier kun je jouw token vandaan halen. 

Hopelijk is de npm install nu klaar. Anders kun je jezelf even vermaken met dit: https://www.youtube.com/watch?v=PLOPygVcaVE

Wanneer dit uiteindelijk klaar ga terug naar de hoofdmap met:
```
cd ../
```
En voer het volgende commando uit:
```
dotnet build
```
Hierna kan de applicatie opgestart worden met het volgende commando:
```
dotnet run
```
Open nu https://localhost:5001 in je browser. Als het goed is krijg je de volgende voorbeeld webapplicatie geopend:
<img src="workshopImages/dotnetExampleReactApp.png" />

Nu kunnen er wat bestanden verwijdert worden die we niet nodig hebben. In de components map binnnen de src van de ClientApp kunnen de volgende bestanden verwijdert worden:
* Counter.js
* FetchData.js
* Layout.js
* NavMenu.js
* NavMenu.css

Het bestand Home.js kunnen de regels 4 en 9 t/m 22 verwijdert worden om zo een leeg Home component over te houden die we zo gaan opvullen. Als laatste moet de App.js nog aangepast worden. De return binnen de render methode van App.js kan leeggehaald worden en vervangen worden met:
```js
<Home />
```
Vervolgens moeten ook nog de nu onnodige imports verwijdert worden.

Als het goed is ziet de file structure er nu ongeveer als volgt uit:

<img src="workshopImages/fileTree.png">

App.js en Home.js zien er dan als volgt uit:

<img src="workshopImages/appJs.png">

<img src="workshopImages/emptyHomeJs.png">

## Stap 2 Mapbox implementeren
Nu kan er begonnen worden aan het implementeren van mapbox.

Open Home.js in dit bestand wordt dalijk alle code geschreven. 

Voeg boven in het bestand de volgende code toe:
```js
import ReactMapGL from 'react-map-gl'
```

Voeg een constructor toe aan het home component en vul de initial state met de volgende data:

<img src="workshopImages/firstConstructorImage.png">

Hiermee beschrijf je hoe groot je de map wil maken maar ook de startpositie van het viewpoint en de zoom. Met deze coördinaten start het viewpoint op Amsterdam. De nummers in deze state worden constant verandert wanneer de gebruiker zijn locatie op de kaart verandert of zijn zoom verandert. 

Implementeer nu het ReactMapGL component zoals hieronder weergegeven:

<img src="workshopImages/firstMapBoxComponentImage.png">

Let op de "onViewportChange" handler. Dit is de handler die de state verandert wanneer de gebruiker rondbeweegt op de kaart.
mapStyle geeft de gebruiker de optie om het uiterlijk van de kaart te veranderen. Er zijn online een heel aantal styles te vinden maar degene die in deze workshop gebruikt wordt is het meest gebruikelijk. Let er ook op de je hier ook je apiAccestoken moet invullen. Het is natuurlijk een goed idee om die token in een .env bestand te zetten maar voor deze workshop maakt dat niet heel veel uit.

## Stap 3 Layers toevoegen

//TODO