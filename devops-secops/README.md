# DevOps felvételi feladat

* :alarm_clock: **Határidő**: A feladat kiosztását követő **11-ik munkanap** 23:59:59 (CEST)
* **A projektet egy publikus github repository-ba várjuk tőled.**

A feladatot tetszőleges virtualizációs megoldással tudod elkészíteni:
  * Linux KVM - preferált
  * VirtualBox
  * Vmware Workstation
  * etc.
## Megvalósítandó feladat leírása
### Linux "Server" beállítása
A cél egy debian alapú szerver kialakítása manuális telepítéssel

A feladatok különböző nehézségűek. A nehézségi szintek külön vannak jelölve.
A pontozas súlyozása az alábbiak szerint alakul:

  * Egy feladatra kapható maximális pontszám akkor érhető el, ha a feladat teljes egészében elkészült

  * Minden feladat mellett megtalálható az adott pontérték

  * :exclamation:**Részpont van!**
    **Javasoljuk:** a feladatot inkább addig vidd el, amíg tudod, mint hogy semmit nem csinálsz meg belőle.
  * :grey_exclamation:**Nem baj, ha nem megy egy-egy feladat!** 
    _Nem várjuk el tőled, hogy azonnal mindent tudj_ :-) A hozzáállás a lényeg!

**A feladat megoldások dokumentálása és feltöltése**:

  * Githubon egy `gist` létrehozása és oda külön-külön a megírt scriptek, config snippetek, illetve a kiadott parancsok feltöltése
  * Githubon egy repó készítése és oda a szükséges file-ok feltöltése (vagrantfile, ansible playbook, stb.)

#### Linux rendszer telepítése `max. 150 pont`
##### Feladat leírása
A feladat egy debian 11 telepítése, majd egy user felvétele, alap programok telepítése és a folyamat **dokumentálása** a fent leírt módon.

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
	* `fail2ban`telepítése és az 
	  * SSH-ra való bekonfigrálása
	  * valaimt nginx-ra való bekonfigurálása
#### Kiegészítő szolgáltatások telepítése `max. 150 pont`
##### Feladat leírása
A feladat, hogy telepítsük az alábbi szolgáltatásokat:
  - NGINX
  - MariaDB
  - Docker
  - Git
A feladat elvégezhető az OS-en való telepítéssel, vagy akár konténerek futtatásával. ;)

Feladatok:
  * NGINX webszerver telepítése
    * 80-as porton
      * **EXTRA:** HTTPS beállítása, self signed cert-el
	* `Hello UDEMX!` legyen a főoldalon kiírva.
  * MariaDB telepítése
    * default porton
	* **EXTRA:** `udemx` user és hozzá `udemx-db` létrehozása arra a `udemx` user jogosultságának beállítása.
  * Docker telepítése
    * hello-world container futtatáse
    * **EXTRA1:** minden egyéb feladat (MariaDB, NGINX) konténerben fusson
    * **EXTRA2:** minden kontner automatikusan elindul a virtualis géppel
  * Git telepítése
    * udemx@udemx.eu legyen a default user
	* **EXTRA1:** ssh-kulcs alapú git elérés beállítása

#### Nehezebb feladatok plusz pontokért `max. 150 pont`
##### Feladat leírása
Itt olyan feladatok találhatóak, melyek elkészítése nem kézenfekvő. Részpontszám itt is van.
  - Iptables beállítása
      - csak az alkalmazáshoz szükséges portok legyenek nyitva a VM-en.
  - Írni egy-egy külön shell scriptet 
      - egy script, ami mysql dump-ot készít az aktuális dátummal elnevezett mappába, majd ezt beállítani cron-ban, hogy naponta hajnali 2-kor fusson le.
      - a 3 legutoljára módosított fájl listázása a`/var/log` mappából a  `mod-<DATE>.out` fájlba
      - 5 napon belül módosított fájlok listázása a `/var/log/*` mappákból rekurzívan a  `last_five-<DATE>.out` fájlba
      - A `/proc/loadavg`-ból a 15 perces érték kiíratása a `loadavg-<DATE>.out` fájlba
      - Az NGINX default konfigurációs fájljában az alábbi sztringben `<title>Welcome to nginx!</title>` cseréljük le a`<title>`-t `Title:` -ra és a `</title>`-t ne bántsuk.

  - Docker project feladat
     - Tetszőleges alkalmazás (pl: github laravel demo project) életrekeltése docker compose-al külön db-vel és web kiszolgálóval.
     - +1: vim-ből kilépés parancsa :) :) :)

#### CI-CD feladat `max. 150 pont`
##### Feladat leírása:
  * Jenkins szerver telepítése és beállítása
  * Pivát Docker registry létrehozása webes ui felülettel
  * A kapott privát Github repository használható a projekthez / vagy egy másikat is létre lehet hozni tetszés szerint
	
###### Jenkins telepítése dockerben és alap beállítások	
  * A jenkins szerver telepítése dockerban 
  * Egy worker node létrehozása a hoszton / egy másik konténeren

###### Privát Docker registry telepítése dockerben
  * Két docker konténert kell indítani:
  * Docker Registry
  * Docker Registry UI

###### Githubon egy privát repó és egy új projekt létrehozása

 * A Repository-ba egy projekt létrehozása - Hello World http server / tetszőleges más webes alkalmazás
 * A projekt tartalmazzon egy dockerfile-t, amivel elkészíthető a szükséges docker image

###### Jenkins job létrehozása
 * A feladathoz tetszőlegesen készíthető jenkins job:
   
   Követelmények:
   
   * scm: itt lehet beállítani a privát github repó-t 
   * build: a Dockerfile alapján az alkalmazásból készüljön egy docker image, amit a létrehozott registry-be pusholunk fel
   * deploy: kiteszi az alkalmazást a szerverre a registry-be felpusholt image-ből
   
   Ötletek
   
   A feladat végrehajtható akár egy job-ban, amiben a post build sikeres build esetén deploy-olja az alkalmazást, vagy akár két job-ban is
   Bármilyen techonlógia használható, a jenkins nagy szabadságot ad (ansible, shell script stb.)

* **EXTRA:** a feladat megoldása pipeline vagy jenkinsfile segítségével, nem sima freestyle job-ként

#### Automatizáció feladat `max. 150 pont`
##### Feladat leírása:
A fentebb leírtak elkészítése tetszőlegesen kiválasztott `configuration management` / IaC tool segítségével.

1. A Server telepítés automatizálása pl. `Vagrant` segítségével
2. A különböző alakalmazások telepítése, konfigurálás, illetve a scriptek létrehozása `ansible` segítségével
3. A CI/CD feladat megoldása `ansible` segítésével
   **EXTRA:** Jenkins automatizált configurálása `ansible` segítségével a manuálisan elkészített config alapján

A cél, hogy a repository klónozása után egy vagrant up parancs kiadását követően a fenti feladatok automatikusan valósuljanak meg az alábbi formában:
 * OS, alkalmazások és a szükséges dependenciák telepítése
 * szükséges konfigurációk beállítása (sshd, fail2ban, mysql, nginx, stb)
 * scriptek futtatása és a .out file-ok létrehozása a /opt/scripts mappába
 * CI/CD környezet telepítése (+ EXTRA: automatizált config)

Feladat beadása:
Az elkészült `vagrantfile`, `ansible` playbook és egyéb configok feltöltése a git repository-ba.
