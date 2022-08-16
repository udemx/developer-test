# Mobile development felvételi fejlesztési feladat

* :alarm_clock: **Határidő**: A feladat kiosztását követő **11-ik munkanap** 23:59:59 (CEST)
* **A projektet egy publikus github repository-ba várjuk tőled.**
* :exclamation:**Részpont van!**
  **Javasoljuk:** Inkább a feladatot addig vidd el, amíg tudod, mint hogy semmit nem csinálsz meg belőle.
  * :grey_exclamation:**Nem baj, ha nem megy egy-egy feladat!** 
    _Nem várjuk el tőled, hogy azonnal mindent tudj_ :-) A hozzáállás a lényeg!

## Grandma’s ice cream
A cél egy olyan alkalmazás fejlesztése, amelyen keresztül a felhasználó fagylaltokat tud rendelni.

Az applikáció egy távoli kiszolgálóval kommunikál, JSON formátumban. HTTP hívások segítségével kérhetjük le a termékeket az alábbiak szerint:

### Fagylaltok
[icecreams.json](https://raw.githubusercontent.com/udemx/hr-resources/master/icecreams.json)

Az elérhető fagylaltok kérhetőek le. Séma az alábbiak szerint:

```json
{
  "iceCreams" : [IceCream], // array of iceCream objects
  "basePrice" : Double // the base price of an ice cream
}
```

Ahol az `IceCream` definíció: 

```json
{
  "name" : String, // Display name
  "status" : Status, // availability status
  "imageUrl" : String // Optional image url
}
```

A `Status` a következő értékeket veheti fel: 
  * `available`,  - címke: elérhető
  * `melted`, - címke: kifogyott
  * `unavailable`,. -. címke: nem is volt.

### Extras
[extras.json](https://raw.githubusercontent.com/udemx/hr-resources/master/extras.json)

A fagylaltokhoz elérhető extrák listája: 

```json
[{
  "type" : String, // display name of an Extra’s type
  "required" : Boolean, // optional. If true, selection required
  "items" : [Item] // array of Item object
}]
```

Ahol az `Item` a következő: 

```json
{
  "id" : Long, // unique identifier
  "name" : String, // display name
  "price" : Double // additional price
}
```

A fagylaltokat egy listában kell megjeleníteni, ahol a felhasználó böngészni tud a lehetőségek között. A listát státusz szerint tudja rendezni. A kívánt fagyi kiválasztása után, meg kell jeleníteni egy interfészt, ahol kérhető tetszőleges extra a fagyihoz (pl.: édes tölcsérben, csokiöntettel).

Ha a fagyik a kosárba kerültek, a felhasználó le tudja adni a rendelését. Lehetőséget kell biztosítani bármely elem eltávolítására a kosárból.

### Rendelés
A rendelés leadása a következő végpont hívásával lehetséges:

[http://httpbin.org/post](http://httpbin.org/post)

A `Body` adat sémája: 

```json
[{
  "id" : Long, // id of an iceCream
  "extra" : [Long] // array of extra’s ids
}]
```

## Elvárások:
  * Nem szükséges minden egyes feladatot megoldani. Törekedj arra, hogy a legjobb tudásod szerint old meg azt ami elkészül. A megoldás során bármilyen eszközt használhatsz.
  * A UI, kivitelezése a [minta](grandmas-homemade-ice-cream.pdf) alapján. A hiányzó képernyők saját kezű kialakítása. A ikonok és egyéb források az [assets/](assets/) mappában találhatóak.
  * Ajánlott programozási nyelv: Android - Kotlin, iOS - Swift5.

## Feladatok
  * A fagyik megjelenítése listán a design alapján.
  * Fagyi kiválasztása, hozzáadása a kosárhoz.
  * Extrák képernyő kialakítása, a hozzáadás folyamatának kiegészítése. 
  * Rendelés leadása

## Szorgalmi feladatok
  1. Tetszőleges Fagyi / Extra eltávolítása a kosárból
  2. A fagyik rendezhetősége status alapján
  3. Kosárban lévő elemek számának megjelenítése a kosár ikonon
  4. Aktuális kosár perzisztálása applikáció indítások között.

Jó Munkát Kívánunk!

![](https://raw.githubusercontent.com/udemx/hr-resources/master/images/bud.jpg)

