# DevOps felvételi feladat

* :alarm_clock: **Határidő**: A feladat kiosztását követő **11-ik munkanap** 23:59:59 (CEST)
* **A projektet egy publikus github repository-ba várjuk tőled.**

## Megvalósítandó feladat leírása
### Linux VPS beállítása VirtualBox környezetbe
A cél egy debian alapú szerver kialakítása [VirtualBox](https://www.virtualbox.org/) környezetben.

A feladatok különböző nehézségűek. A nehézségi szintek külön vannak jelölve.
Pontozas súlyozása az alábbiak szerint alakul:
  * Egy feladatra kapható maximálsi pontszám akkor érhető el, ha a feladat teljes egészében elkészült

  * Minden feladatra az adott feladat mellet található pontérték érhető el. 

  * :exclamation:**Részpont van!**
    **Javasoljuk:** Inkább a feladatot addig vidd el, amíg tudod, mint hogy semmit nem csinálsz meg belőle.
  * :grey_exclamation:**Nem baj, ha nem megy egy-egy feladat!** 
    _Nem várjuk el tőled, hogy azonnal mindent tudj_ :-) A hozzáállás a lényeg!

**Beadandóak a Virtualbox adatfájlok feltöltése** (a forrás mappát levélben küljök ki):
  * `*.vbox` - VirtualBox Machine settings file.
  * `*.vdi/vmdk/vhd/hdd` - VirtualBox disk image file

#### Linux rendszer telepítése `max. 150 pont`
##### Feladat leírása
A feladat egy debian 11 telepítése, user felvétele és alap programok telepítése és a folyamat **dokumentálása** egy _README.MD_ fájlba. A file-t ide a REPO-ba kell elkészíteni.

Feladatok:
  * Debian 11 telepítése
    * root jelszó: Alma1234
    * saját user létrehozása
    * **EXTRA:** a `/opt` és a `/tmp` külön partícióra kerüljön
  * Linux beállítása
    * `sudo` telepítése
    * Midnight Commander telepítése
    * `htop` telepítése
    * OpenJDK 8 és OpenJDK 11 telepítése
    * **EXTRA:** Állítsd a `javac` verzióját OpenJDK 8-ra.
    * `udemx` user létrehozása
      * **EXTRA:** a `udemx` user home mappája legyen a `/opt/udemx` mappában.
    * `ssh` elérés beállítása
      * **EXTRA1:** az ssh portja ne a default port legyen
      * **EXTRA2:** PEM alapú belépés jelszó helyett
	
#### Kiegészítő szolgáltatások telepítése `max. 150 pont`
##### Feladat leírása
A feladat, hogy telepítsük az alábbi szolgáltatásokat:
  - Apache HTPPD
  - MariaDB
  - Docker
  - Git
A feladat elvégezhető az OS-en való telepítéssel, vagy akár konténerek futtatásával. ;)

Feladatok:
  * Apache HTTPD telepítése
    * 80-as porton
      * **EXTRA:** HTTPS beállítása, self signed cert-el
	* `Hello UDEMX!` legyen a főoldalon kiírva.
  * MariaDB telepítése
    * default porton
	* **EXTRA:** `udemx` user és hozzá `udemx-db` létrehozása arra a `udemx` user jogosultságának beállítása.
  * Docker telepítése
    * hello-world container futtatáse
    * **EXTRA1:** minden egyéb feladat (MariaDB, HTTPD) konténerben fusson
    * **EXTRA2:** minden kontner automatikusan elindul a virtualis géppel
  * Git telepítése
    * udemx@udemx.eu legyen a default user
	* **EXTRA1:** ssh-kulcs alapú git elérés beállítása
	
#### Extra feladatok plusz pontokért `max. 150 pont`
##### Feladat leírása
Itt olyan feladatok találhatóak, melyek elkészítése nem kézenfekvő. Részpontszám itt is van.
  - Iptables beállítása, 
  - hogy csak az alkalmazáshoz szükséges portok legyenek nyitva a VM-en.
  - Írni egy shell scriptet 
  - ami mysql dump-ot készít az aktuális dátummal elnevezett mappába és ezt beállítani cron-ban, hogy naponta hajnali 2-kor fusson le.
  - 3 legutoljára módosított fájl listázása
  - 5 napon belül módosított fájlok listázása
  - adott mappa alatt összes:
  - php-ra syntax ellenőrzés futtatása
  - fájlra md5 checksum számítása
  - /proc/loadavg-ből a 15 perces érték kiíratása
  - A következő stringben a `<title>` cseréljük le `Title:` -raés a `</title>`-t ne bántsuk. Eredeti string: `<title>About the Web</title>`

Extra-extra feladatok:
  - Tetszőleges alkalmazás (pl: github laravel demo project) életrekeltése docker compose-al külön db-vel és web kiszolgálóval.
  - Docker-ből indított tetszőleges app nginx proxy-n keresztül elérhetővé tétele LetsEncrypt-es SSL használatával úgy, hogy az ssllabs teszten A+ besorolást kapjon.
  - Sávszélkorlátos backup script írása, ami A-ból B-be átmozgatja az állományokat és garantálja, hogy B oldalon byte-ra egyezik minden.

  +1: vim-ből kilépés parancsa :) :) :)

#### CI-CD Extra feladat plusz pontokért `max. 150 pont`
##### Feladat leírása:
  * Jenkins szerver telepítése és beállítása
  * Pivát Docker registry létrehozása webes ui felülettel
  * Github repository és projekt létrehozása
	
###### Jenkins telepítése dockerben és alap beállítások	
  * A szerveren létre kell hozni a jenkins felhasználót, amit majd a jenkins szerver fog használni, amikor bejelentkezik a node-ra

###### Privát Docker registry telepítése dockerben
  * Két docker konténert kell indítani:
  * Docker Registry
  * Docker Registry UI

###### Githubon egy privát repó és egy új projekt létrehozása 
 * Ki kell klónozni majd feltölteni a létrehozott privát repó-ba egy tetszőleges Hello World http server projektet a github-ról.
   Szükség van rá, hogy ez tatalmazon egy dockerfile-t, amivel meg tudjuk, majd építeni az image-t

###### Jenkins jobok létrehozása
 * A feladathoz két jenkins job-ra lesz szükség, az első le buildeli a hello world docker image-t, a második elindítja azt:
   * Új freestyle projekt létrehozása jenkins-ben:
   A build step alatt egy execute shell-t kell létrehozni, a script:
   először lehúzza az image-t a registry-ből, majd elindítja
   Öteltek, magyarázatok:
   
   >Az scm alatt kell állítani a létrehozott privát github repó-t build step alatt egy execute shell-t kell létrehozni és meg kell írni egy kis build scriptet:
   A Dockerfile alapján megépíti az hello world alkalmazás image-t és fel pusholja a  létrehozott docker registry-be Post-build action alatt meg kell adni egy másik (downstream) projectet, ami elindítja a build során készített image-t.

* **EXTRA:** a feladat megoldása pipeline vagy jenkinsfile segítségével
