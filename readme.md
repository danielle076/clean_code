## Waarom clean code?

- code schrijven bestaat vooral uit (andermans) code lezen
- een project bevindt zicht 80% van de tijd in de onderhoudsfase
- je bent nooit de enige programmeur die aan een project werkt
- verhoogt onderhoudbaarheid en uitbreidbaarheid van de applicatie
- voorkomt vertraging/stilstand van nieuwe features

## Naamgeving

Hoe noem je je `packages`, `klassen`, `methodes` en `variabelen`.

Met Java hebben we de conventie geleerd. Klassen/objecten schrijf je met een hoofdletter, alles wat volgt met CamelCase. Methodes/variabelen schrijf je met kleine letters.

Naast de conventie is het van belang hoe je dingen noemt. Ga geen dingen `x`, `y`, `z` noemen, `firstName` en `lastName` is beter. 

### Conventie

Java gebruikt CamelCase als praktijk voor het schrijven van namen van methoden, variabelen, klassen, packages en constanten.

<i>Camelcase in Java:</i> bestaat uit samengestelde woorden of zinnen zodanig dat elk woord of afkorting begint met een hoofdletter of het eerste woord met een kleine letter, de rest allemaal met een hoofdletter.

<b>1. Klassen en interfaces </b>
* Klassenamen moeten <b>zelfstandige naamwoorden</b> zijn, met de <b>eerste</b> letter van elk woord in hoofdletters. Interfaces moeten ook een hoofdletter krijgen.
* Gebruik hele woorden en vermijd acroniemen en afkortingen.

      interface Bicycle
      class MountainBike implements Bicyle
    
      interface Sport
      class Football implements Sport

<b>2. Methoden</b>
* Methoden moeten <b>werkwoorden</b> zijn, met de <b>eerste letter kleine letters</b> en de eerste letter van elk volgende woord in hoofdletters.

        run ();
        runFast();
        getBackground();

<b>3. Variabelen</b> 
* Variabelen kunnen beginnen met underscore('_') of dollarteken '$', maar dat wordt niet aanbevolen.
* Variabelen moeten kort en betekenisvol zijn.
* Ze moeten mnemotechnisch zijn, d.w.z. ontworpen om aan de toevallige waarnemer de bedoeling van het gebruik aan te geven. 
* <b>Variabelenamen van één teken moeten worden vermeden</b> behalve voor tijdelijke variabelen.
* Veel voorkomende namen voor tijdelijke `variabelen` zijn `i`, `j`, `k`, `m`, en `n` voor `integers`; `c`, `d`, en `e` voor karakters.

        int i;
        char c;
        float myWidth;

<b>4. Constante variabelen</b>
* Moeten allemaal hoofdletters zijn met woorden gescheiden door underscores ("_").
* Er zijn verschillende constanten die gebruikt worden in voorgedefinieerde klassen zoals Float, Long, String etc.

      static final int MIN_WIDTH = 4;

* Enkele Constante variabelen gebruikt in voorgedefinieerde Float klasse

        publieke statische finale float POSITIVE_INFINITY = 1.0f / 0.0f;
        publieke statische finale float NEGATIEVE_INFINITEIT = -1.0f / 0.0f;
        publieke statische finale float NaN = 0.0f / 0.0f;

<b>5. Packages</b>
* Het voorvoegsel van een unieke pakketnaam is altijd geschreven in kleine letters ASCII en moet een van de top-level domeinnamen zijn, zoals com, edu, gov, mil, net, org.
* De daaropvolgende componenten van de pakketnaam variëren volgens de eigen interne naamgevingsconventies van een organisatie.

        com.sun.eng
        com.apple.quicktime.v2
        java.lang

### Naamgeving

- Klasse en packages zijn `zelfstandige naamwoorden`
- Klasse-, tabel- en packagenamen zijn altijd `enkelvoud`
  - meervoud houd je beschikbaar voor de variabelen die een verzameling bevatten, bijvoorbeeld een list van het type customer noemen we customers
- Methode-namen zijn `werkwoorden` (+ lijdend voorwerp)
  - Methoden doen dingen, bijvoorbeeld `getCustomer`, `saveCustomer`
- Alle namen moeten eenduidig zijn (niet `ambigious`)
- Namen moeten uitleggen of verklaren wat de inhoud is. 
  - Wanneer een lange benaming hierbij helpt moet je dit doen

Niet doen:
- Wees niet grappig
  - code moet strak, zakelijk en duidelijk zijn
- Gebruik geen generieke namen, zoals Manager, Processor, Data etc.
  - deze wordt niet altijd gevolgd
- Voeg geen voorvoegsels (prefix) toe aan klassenamen
- Gebruik geen Hongaarse notatie in de variabele
  - bijv. `long lCount = 8;` of `String sName  "Danielle";`

## Nette methodes

Houd je methodes klein!

Methodes moeten één ding doen. Dit moeten ze goed doen en ze moeten alleen dat doen.

### Stepdown rule

Zorg ervoor dat een methode die een andere methode aanroept boven de aangeroepte methode staat.

We zijn getraind om van boven naar beneden te lezen.

### Aantal argumenten

Probeer het aantal argumenten zo klein mogelijk te houden. Ideaal is nul. Vier of meer is te veel.

Gebruik builder of factory patterns

### Geen flag (boolean) argumenten

Maak geen methodes die iets doen op basis van een te ontvangen boolean - argument. Maak liever twee methodes.

### Command query seperation

Een methode moet een antwoord geven óf een methode moet data wijzigen. 
Niet allebei tegelijk! In andere woorden een methode moet iets aan een object veranderen of een methode moet informatie van het object teruggeven.

## Commentaar

Don't comment bad code. Rewrite it.

Gebruik methode- en variabelenamen om je code begrijpbaar te maken.

```
// Check to see if employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65)) {
// ...
}
// Of
if (employee.isEligibleForFullBenefits()) {
// ...
}
```

### Wanneer niet

- Overtollig commentaar
- Onbedoeld misleidend commentaar
- Bij sluit accolades plaatsen
- Uitgecommentarieerde code
  - Is wel prima bij tijdens ontwikkelen of testen
- Positie-markering 
  - Waar je bent, of vanaf deze regel zijn er getters/setters

### Wanneer wel

- Public API - JavaDoc
  - interactie naar buiten toe
- Legal comments wanneer erom gevraagd wordt, bijvoorbeeld over licenties
- JavaDoc intern (wanneer de opdrachtgever daarom vraagt)
  - nadeel is dat je hem moet bijhouden
- Verduidelijking of verantwoording
- Als waarschuwing
- TODO comments 
  - IntelliJ: `//TODO`

### Boy scout rule

Leave the campground cleaner than you found it.

Kijk wel uit voor het creëren van nieuwe bugs bij het aanpassen.