# BAIN FS25 - Suchmaschinen und Discovery-Systeme I



## Agenda

* Suchmaschinen und Discovery-Systeme Teil 1
  * Vorführung VuFind/Solr-Installation
  * Übung Suche in VuFind vs. Suche in Solr

## Testserver für heute

(Apache: http://X.X.X.X)
VuFind: http://X.X.X.X/vufind/
Vufind Admin: http://X.X.X.X/vufind/Install/Home
Solr: http://X.X.X.X:8983/solr/

## Installation und Konfiguration von VuFind

* VuFind Internetseite: https://vufind.org
* VuFind Code bei GitHub: https://github.com/vufind-org/vufind
* Deutsche VuFind Anwendergemeinschaft: https://vufind.de mit Anwendertreffen
* VuFind-Installationen weltweit: https://vufind.org/wiki/community:installations
  * Beispiel UB Leipzig: https://katalog.ub.uni-leipzig.de
  * Beispiel Nationalbibliothek Finnland: https://finna.fi/?lng=en-gb
  * Beispiel Gemeinsame Verbündeindex [GVI](https://www.agv-gvi.de/ueber-den-gvi/): https://fernleihe.boss.bsz-bw.de/Search/Results?lookfor=test&type=AllFields&hiddenFilters%5B%5D=-consortium%3AFL

**Komponenten**
https://vufind.org/wiki/installation:notes#components
* Webserver Apache
* Suchmaschine Solr
* Webprogrammiersprache PHP (Laminas Framework)
* MySQL Datenbank
* (angedocktes Informationssystem, also z.B. Bibliothekssystem)



### Installation VuFind 10.1.1

Virtuelle Maschine bei einem Cloudhoster.

*Bzgl. **SSH-Authentifizierung** auf dem Server: Siehe Kapitel VIII Kryptografie in Praxishandbuch IT-Grundlagen für Bibliothekare*

Installation nach offizieller Anleitung für VuFind unter Ubuntu: https://vufind.org/wiki/installation:ubuntu


Es folgen die relevanten Auszüge und Hinweise/Erklärungen dazu.

#### Version Requirements

> These instructions were most recently tested on Ubuntu 24.04 LTS (...)


#### Installing VuFind from the DEB Package

> The easiest way to get VuFind up and running is to install it from the DEB package.

VuFind stellt ein Installationspaket bereit. Unter Linux gibt es viele verschiedene Formate für Installationspakete. Für Ubuntu und Debian gibt es DEB, für Fedora und SUSE beispielsweise RPM. Wir starten die Installation wie vorgegeben:

```shell
wget https://github.com/vufind-org/vufind/releases/download/v10.1.1/vufind_10.1.1.deb
sudo dpkg -i vufind_10.1.1.deb
```

Es erscheint eine Fehlermeldung, dass noch nicht alle von VuFind benötigten Pakete installiert sind. Zunächst aktualisieren wir das Paketverzeichnis:

```shell
sudo apt-get update
```

Dann lassen wir die benötigten Pakete mit installieren:

```shell
sudo apt-get install -f
```

#### Important Notes / Database Issues


>  Case 1 - MySQL: If you wish to connect to the root account through the web-based installer in order to set up VuFind®'s database, you should follow these steps:
    Disable the root account's “auth_socket” plugin, which prevents regular logins, by logging in with sudo mysql -uroot and then running the appropriate command for your Ubuntu version:
        Ubuntu 24+: UPDATE mysql.user SET plugin='caching_sha2_password' WHERE User='root'; FLUSH PRIVILEGES;
    Quit the MySQL tool and run sudo /usr/bin/mysql_secure_installation at the command line to automatically improve some database security settings.
    If the mysql_secure_installation process does not automatically help you set a root password, you may wish to do so manually, by logging in with sudo mysql -uroot and then running the appropriate command for your Ubuntu version:
        Ubuntu 24+: ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password by 'your-password-here';
    Edit /etc/mysql/mysql.conf.d/mysqld.cnf, add the appropriate line for your Ubuntu version to the bottom of the file:
        Ubuntu 24+: authentication_policy=caching_sha2_password
    Run sudo service mysql restart before attempting to set up VuFind®. This will ensure that new accounts are created using a PHP-compatible authentication method.




```shell
sudo mysql -uroot -p -e "UPDATE mysql.user SET plugin='caching_sha2_password' WHERE User='root'; FLUSH PRIVILEGES;"
```


```shell
sudo /usr/bin/mysql_secure_installation
```

* Das aktuelle Passwort ist leer (Enter drücken).
* Evtl. Neues Passwort vergeben (und merken!).
* Die voreingestellten Antworten sind OK (alle Fragen können mit Enter bestätigt werden).

```shell
sudo echo "authentication_policy=caching_sha2_password" >> /etc/mysql/mysql.conf.d/mysqld.cnf
[vmware: sudo sh -c 'echo "authentication_policy=caching_sha2_password" >> /etc/mysql/mysql.conf.d/mysqld.cnf']
sudo service mysql restart
```

#### Important Notes / (Ende)

> You may want to restart your system one more time to be sure all the new settings are in place, or at least make sure appropriate environment variable settings are loaded by running: `source /etc/profile`

Ein Neustart ist in unserem Fall nicht erforderlich. Es reicht aus, den genannten Befehl einzugeben:

```shell
source /etc/profile
```

#### Configuring and starting VuFind / Start solr

Ggf. öffentlicher Zugriff auf Solr einstellen (0.0.0.0):

```shell
nano /usr/local/vufind/solr/vendor/bin/solr.in.sh
```

Solr starten (mit Parameter `-force` bei Testinstallation mit root user):

```shell
/usr/local/vufind/solr.sh -force start
```

Die Warnungen zu den Limits können erstmal ignoriert werden. In der Doku von VuFind ist beschrieben, wie sich das korrigieren liesse: <https://vufind.org/wiki/administration:starting_and_stopping_solr>

#### Configuring and starting VuFind / Configure VuFind

> Open a web browser, and browse to this URL: <http://your-server-name/vufind/Install/Home> (Replace “your-server-name” with the address you wish to use to access VuFind; replace “vufind” with your custom base path if you changed the default setting during installation).

http://X.X.X.X/vufind/Install/Home

#### Configuring and starting VuFind / Auto-Configuration

> If installation was successful, you should now see an Auto Configure screen. Some items on the list will be marked “Failed” with “Fix” links next to them. Click on each Fix link in turn and follow the on-screen instructions. (...) After an issue is successfully resolved, you can click the “Auto Configure” breadcrumb to go back to the main list and proceed to the next problem.

Die meisten Punkte können ohne weitere Angaben "gefixt" werden. Nur die beiden Punkte Database und ILS erfordern weitere Angaben.

#### Configuring and starting VuFind / Auto-Configuration / Database

Bei der Datenbank muss ein neues Passwort vergeben sowie das zuvor oben im Abschnitt "MariaDB Passwort für root" eingegeben werden (bei mir leer).

#### Configuring and starting VuFind / Auto-Configuration / ILS

Wir haben kein Bibliothekssystem, daher wählen wir NoILS. Dann wird aber trotzdem noch "Failed" angezeigt und wenn wir nochmal auf "Fix" klicken erscheint die folgende Meldung:

> (...) You may need to edit the file at /usr/vufind/local/config/vufind/NoILS.ini

```shell
sudo sed -i 's/mode = ils-offline/mode = ils-none/' /usr/local/vufind/local/config/vufind/NoILS.ini
```

#### Weitere Sicherheitseinstellungen

* Die in den Abschnitten [Locking Down Configurations](https://vufind.org/wiki/installation:ubuntu#locking_down_configurations) und [4. Secure your system](https://vufind.org/wiki/installation:ubuntu#secure_your_system_and_prepare_for_production) beschriebenen Einstellungen benötigen wir für unsere Testinstallation nicht.

### Testimport

* Ohne Inhalte lässt sich VuFind schlecht erproben. Daher laden wir zunächst ein paar Daten in das System.
* VuFind liefert für Tests einige Dateien mit. Wir laden einige davon im MARC21-Format.

```shell
/usr/local/vufind/import-marc.sh /usr/local/vufind/tests/data/journals.mrc
/usr/local/vufind/import-marc.sh /usr/local/vufind/tests/data/geo.mrc
/usr/local/vufind/import-marc.sh /usr/local/vufind/tests/data/authoritybibs.mrc
```

* Anschliessend sollten in der Suchoberfläche unter http://X.X.X.X/vufind ca. 250 Datensätze enthalten sein.


## Funktion von Suchmaschinen am Beispiel von Solr

### Zur Einordnung von Solr

* Solr ist zusammen mit Elasticsearch quasi "Industriestandard".
* Üblicherweise sollte vor dem Import der Daten in einem Schema festgelegt werden welche Felder existieren und welche Datentypen diese beinhalten dürfen.
* Solr hat zwar eine integrierte Suchoberfläche, aber diese ist nur zu Demo-Zwecken gedacht.
* Das Discovery-System VuFind basiert auf Solr (ebenso wie viele kommerzielle Lösungen wie z.B. Primo VE).

### Suchindex (Solr) oder Datenbank (MySQL)?

| Solr                     | MySQL                   |
| ------------------------ | ----------------------- |
| flache Dokumente         | relationale Datensätze  |
| lexikalische Suche       | reiner Zeichenvergleich |
| keine Konsistenzprüfung  | Transaktionssicherheit  |
| statische Daten          | veränderliche Daten     |
| -> **Retrieval** (Suche) | -> **Storage** (CRUD)   |

* [CRUD](https://de.wikipedia.org/wiki/CRUD): **C**reate, **R**ead, **U**pdate, **D**elete

### Horizontale vs. Vertikale Suchmaschine

* Horizontal: unspezifische Suche über heterogene Datenbestände
    * erfordert kein Datenschema ("schema-less")
    * erlaubt keine semantischen Abfragen oder Feldsuchen
    * Beispiele: Internetsuche, Volltextsuche
* Vertikal: datenmodell-orientierte Suche über homogene Datenbestände
    * erfordert ein Datenschema
    * erfordert häufig Datenprozessierung zur Homogenisierung
    * Beispiele: Bibliothekskatalog, Online-Shop

### Sichtung von Solr in VuFind

* Administrationsoberfläche: http://X.X.X.X:8983/solr/
* Bibliografische Daten im Index "biblio" links
    * Files > stopwords
    * Technische Suchoberfläche > query
    * Schema des Index > schema
  * Erläuterung der VuFind-Felder in 

### Übung: Suche in VuFind vs. Suche in Solr

* Suchen in VuFind: http://X.X.X.X/vufind
  * Beispielsweise nach `psychology`
* Suchen in Admin-Oberfläche von Solr: http://X.X.X.X.X:8983/solr/#/biblio/query
  * im Feld q mit Feldname:Suchbegriff. Beispiel: `allfields:psychology`
  * unten links Button "Execute Query"
* Probieren sie verschiedene Einstellungen und Suchen aus, vgl: [Dokumentation Solr](https://solr.apache.org/guide/7_0/common-query-parameters.html) und [VuFind Felder](https://vufind.org/wiki/development:architecture:solr_index_schema)
* Notieren Sie Unterschiede und Auffälligkeiten im gemeinsamen Dokument


#### Gruppe 1: 
*
#### Gruppe 2: 
*
#### Gruppe 3: 
*
#### Gruppe 4: 
*

#### Sonstiges

Note:
- Logdatei von Solr anschauen im Terminal (hier sind side Queries gespeichert)

```shell
less +F /usr/local/vufind/solr/vufind/logs/solr.log
```

Beispiel für einen Logeintrag bei einer leeren Suche:
```
2023-05-16 15:47:47.236 INFO  (qtp762074108-39) [ x:biblio] o.a.s.c.S.Request webapp=/solr path=/select params={mm=0%25&facet.field=topic_facet&facet.field=institution&facet.field=building&facet.field=format&facet.field=callnumber-first&facet.field=author_facet&facet.field=language&facet.field=genre_facet&facet.field=era_facet&facet.field=geographic_facet&facet.field=publishDate&spellcheck.dictionary=default&qt=edismax&hl=true&json.nl=arrarr&fl=*&start=0&sort=score+desc,id+asc&rows=20&hl.simple.pre={{{{START_HILITE}}}}&facet.limit=30&q=*:*&spellcheck.q=&hl.simple.post={{{{END_HILITE}}}}&spellcheck=true&qf=title_short^750+title_full_unstemmed^600+title_full^400+title^500+title_alt^200+title_new^100+series^50+series2^30+author^300+contents^10+topic_unstemmed^550+topic^500+geographic^300+genre^300+allfields_unstemmed^10+fulltext_unstemmed^10+allfields+fulltext+description+isbn+issn+long_lat_display&facet.mincount=1&hl.fl=title_short,title_full_unstemmed,title_full,title,title_alt,title_new,series,series2,author,contents,topic_unstemmed,topic,geographic,genre,allfields_unstemmed,fulltext_unstemmed,allfields,fulltext,description,isbn,issn,long_lat_display&facet=true&wt=json&facet.sort=count} hits=250 status=0 QTime=5
```


### Exkurs: Ranking-Kriterien 
* Grad der Übereinstimmung zwischen Suchanfrage und Informationen in Datensatz (tf-idf-Bewertungsmodell)​
    * Term Frequency (ein Dokument im Korpus) * Inverse Document Frequency (alle Dokument im Korpus): https://en.wikipedia.org/wiki/Tf%E2%80%93idf#Motivations
* Wissenschaftliche Bedeutung einer Ressource (z.B. Publikation in peer-reviewed Journal)​
* Relevanz einer Ressource hinsichtlich des Typs der Suchanfrage (z.B. known-item search oder broad-topic search)​
* Erscheinungsdatum einer Ressource​

Frage: Unbehagen bezüglich der Sortierung der Treffer?

Ranking [Primo VE ](https://knowledge.exlibrisgroup.com/Primo/Product_Documentation/020Primo_VE/Primo_VE_(English)/040Search_Configurations/Configuring_the_Ranking_of_Search_Results_in_Primo_VE)
 ![image](https://hackmd.io/_uploads/SyEIrji1xx.png)

### Exkurs: Deduplication and FRBR
#### Dedup
*    Eliminieren von redundanten Daten​​

* Abgleich von Duplikaten basiert in Primo auf der Erstellung eines Dedup-Vektors für jeden Datensatz​​

* Die Vektoren enthalten sogenannte Keys, die den Datensatz identifizieren​​

* Berücksichtigte Felder: Bsp. Titel, Urheberangaben, Identifier ​

* Übereinstimmung  ---> In UI: Anzeige als ein einziger Datensatz 

#### Functional Requirements for Bibliographic Records

* Gruppierung von Dokumenten​

* Verfahren wie bei Dedup, aber Keys basieren nur auf Titel- und Urheberinformationen​

* keine Übereinstimmung –> Einzelrecord​

* Match --> Zuweisung zu FRBR-Gruppe

​​

### Literatur

* Das offizielle Handbuch zu Solr beinhaltet ein gutes Tutorial (ca. 2 Stunden): <https://solr.apache.org/guide/solr/latest/getting-started/solr-tutorial.html>
* Offizielles Handbuch zu VuFind: https://github.com/vufind-org/learning-vufind-book/releases/download/v1.1.2/LearningVuFind.pdf
