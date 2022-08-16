# Frontend development felvételi fejlesztési feladat

* :alarm_clock: **Határidő**: A feladat kiosztását követő **11-ik munkanap** 23:59:59 (CEST)
* **A projektet egy publikus github repository-ba várjuk tőled.**

## Megvalósítandó feladat leírása

### Autókölcsönző alkalmazás

Egy egyszerű autókölcsönző alkalmazást kell elkészíteni.

Pontozás súlyozása az alábbiak szerint alakul:

* Egy feladatra kapható maximális pontszám akkor érhető el, ha a feladat teljes egészében elkészült

* Minden feladatra az adott feladat mellet található pontérték érhető el. 

* :exclamation:**Részpont van!**

  **Javasoljuk:** Inkább a feladatot addig vidd el, amíg tudod, mint hogy semmit nem csinálsz meg belőle.

* :grey_exclamation:**Nem baj, ha nem megy egy-egy feladat!** 
  _Nem várjuk el tőled, hogy azonnal mindent tudj_ :-) A hozzáállás a lényeg!

#### Publikus felület `max. 150 pont`

#### Feladat leírása:

A feleadat egy publikus felület készítése, ahol
* keresni tud az autók között
* le tudja foglalni az adott autót az adatai megadásával. 

_A felületek design-ját és layout-ok megvalósítását rád bízzuk_

#### Megvalósítandó feladatok:

_Kereső felület_

1. Publikus felületen a főoldalon a felhasználó kiválaszt egy valamilyen _daterange picker_-ből egy **_-tól_** és egy **_-ig_** dátumot.
2. Megjelenít egy **listát** az abban az időszakban szabad autókról, képpel, napi árral.

_Foglalás kezelése_

3. A kiválasztott autóra kattintva egy felületen megadja az adatait:
* Név,
* email cím,
* cím,
* telefonszám
* foglalandó napok száma
* foglalás teljes összege (a foglalandó napok számától függ!)

4. Majd egy submit gomb megnyomásával véglegesíti a rendelést.

_Tesztek_

5. min. 50%-os teszt lefedettség

### Admin felület `max. 150 pont`

#### Feladat leírása:

Admin felület egy minimális adminisztrációhoz.

*  `/admin` path-on nem publikus adminisztációs felület megvalósítása

Az admin oldalon szeretnénk

* látni a foglalásokat egy listában
* szerkeszteni autokat (akár újakat felvenni, meglévő adatokat szerkeszteni)

#### Megvalósítandó feladatok:

_Foglalási adatok megjelenítése_

6. Admin belépés
7. Felület ahol láthatjuk a foglalásokat

_Autók szerkesztése_

8. Meglévő autók szerkesztése
9. Új autó felvitele

_Tesztek_

10. min. 50%-os teszt lefedettség

## Javasolt technológiai stack:

* [Vue.JS](https://vuejs.org/) - **preferált** 
  vagy 
* [Angular 11+](https://angular.io/)

* Valamilyen CSS keretrendszer (Bootstrap vagy Bulma) 
  vagy 
* Material design használata

* :information_source: Mivel ez egy Frontend-es feladatsor, így elegendő valamilyen JSON mock szerver használata az adatok eléréséhez
