---
title: BAIN FS25 - Suchmaschinen und Discovery-Systeme | Installation

---

# BAIN FS25 - Suchmaschinen und Discovery-Systeme | Installation



## Agenda

* Suchmaschinen und Discovery-Systeme Teil 1
  * Vorführung VuFind/Solr-Installation
  * Übung Suche in VuFind vs. Suche in Solr

## Testserver für heute

VuFind: http://X.X.X.X/vufind/
Solr: http://X.X.X.X:8983/solr/

## Installation und Konfiguration von VuFind

* VuFind Internetseite: https://vufind.org
* VuFind Code bei GitHub: https://github.com/vufind-org/vufind
* Deutsche VuFind Anwendergemeinschaft: https://vufind.de mit Anwendertreffen
* VuFind-Installationen weltweit: https://vufind.org/wiki/community:installations
  * Beispiel TU Hamburg: https://katalog.tub.tuhh.de
  * Beispiel UB Leipzig: https://katalog.ub.uni-leipzig.de

### Installation VuFind 10.1.1

Installation nach offizieller Anleitung für VuFind unter Ubuntu: https://vufind.org/wiki/installation:ubuntu

Es folgen die relevanten Auszüge und Hinweise/Erklärungen dazu.

#### Version Requirements

> These instructions were most recently tested on Uubntu 24.04 LTS (...)


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

Bei der Datenbank muss ein neues Passwort vergeben sowie das zuvor oben im Abschnitt "MariaDB Passwort für root" eingegeben werden.

#### Configuring and starting VuFind / Auto-Configuration / ILS

Wir haben kein Bibliothekssystem, daher wählen wir NoILS. Dann wird aber trotzdem noch "Failed" angezeigt und wenn wir nochmal auf "Fix" klicken erscheint die folgende Meldung:

> (...) You may need to edit the file at /usr/vufind/local/config/vufind/NoILS.ini

```shell
sudo sed -i 's/mode = ils-offline/mode = ils-none/' /usr/local/vufind/local/config/vufind/NoILS.ini
```

#### Weitere Sicherheitseinstellungen

* Die in den Abschnitten [Locking Down Configurations](https://vufind.org/wiki/installation:ubuntu#locking_down_configurations) und [4. Secure your system](https://vufind.org/wiki/installation:ubuntu#secure_your_system) beschriebenen Einstellungen benötigen wir für unsere Testinstallation nicht.

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

* Zur Einordnung von Solr
* Sichtung von Solr in VuFind

### Zur Einordnung von Solr

* Solr ist zusammen mit Elasticsearch quasi "Industriestandard".
* Üblicherweise sollte vor dem Import der Daten in einem Schema festgelegt werden welche Felder existieren und welche Datentypen diese beinhalten dürfen.
* Solr hat zwar eine integrierte Suchoberfläche, aber diese ist nur zu Demo-Zwecken gedacht.
* Das Discovery-System VuFind basiert auf Solr (ebenso wie viele kommerzielle Lösungen wie z.B. Ex Libris Primo).

### Suchindex (Solr) oder Datenbank (MySQL)?

| Solr                     | MySQL                   |
| ------------------------ | ----------------------- |
| flache Dokumente         | relationale Datensätze  |
| lexikalische Suche       | reiner Glyphenvergleich |
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
* Bibliografische Daten im Index "biblio": http://X.X.X.X:8983/solr/#/biblio
* Technische Suchoberfläche in Solr für Index "biblio": http://X.X.X.X:8983/solr/#/biblio/query
* Schema des Index "biblio": http://X.X.X.X:8983/solr/#/biblio/schema>
  * Erläuterung der VuFind-Felder in VuFind Doku: <https://vufind.org/wiki/development:architecture:solr_index_schema>

### Übung: Suche in VuFind vs. Suche in Solr

* Suchen in VuFind: http://X.X.X.X/vufind
  * Beispielsweise nach `psychology`
* Suchen in Admin-Oberfläche von Solr: http://X.X.X.X.65:8983/solr/#/biblio/query
  * im Feld q mit Feldname:Suchbegriff. Beispiel: `allfields:psychology`
  * unten links Button "Execute Query"
* Notieren Sie Unterschiede und Auffälligkeiten im gemeinsamen Dokument

Note:
- Logdatei von Solr anschauen im Terminal

```shell
less +F /usr/local/vufind/solr/vufind/logs/solr.log
```

Beispiel für einen Logeintrag bei einer leeren Suche:
```
2023-05-16 15:47:47.236 INFO  (qtp762074108-39) [ x:biblio] o.a.s.c.S.Request webapp=/solr path=/select params={mm=0%25&facet.field=topic_facet&facet.field=institution&facet.field=building&facet.field=format&facet.field=callnumber-first&facet.field=author_facet&facet.field=language&facet.field=genre_facet&facet.field=era_facet&facet.field=geographic_facet&facet.field=publishDate&spellcheck.dictionary=default&qt=edismax&hl=true&json.nl=arrarr&fl=*&start=0&sort=score+desc,id+asc&rows=20&hl.simple.pre={{{{START_HILITE}}}}&facet.limit=30&q=*:*&spellcheck.q=&hl.simple.post={{{{END_HILITE}}}}&spellcheck=true&qf=title_short^750+title_full_unstemmed^600+title_full^400+title^500+title_alt^200+title_new^100+series^50+series2^30+author^300+contents^10+topic_unstemmed^550+topic^500+geographic^300+genre^300+allfields_unstemmed^10+fulltext_unstemmed^10+allfields+fulltext+description+isbn+issn+long_lat_display&facet.mincount=1&hl.fl=title_short,title_full_unstemmed,title_full,title,title_alt,title_new,series,series2,author,contents,topic_unstemmed,topic,geographic,genre,allfields_unstemmed,fulltext_unstemmed,allfields,fulltext,description,isbn,issn,long_lat_display&facet=true&wt=json&facet.sort=count} hits=250 status=0 QTime=5
```

#### Gruppe 1: 



### Literatur

* Das offizielle Handbuch zu Solr beinhaltet ein gutes Tutorial (ca. 2 Stunden): <https://solr.apache.org/guide/solr/latest/getting-started/solr-tutorial.html>
* Offizielles Handbuch zu VuFind: https://github.com/vufind-org/learning-vufind-book/releases/download/v1.1.2/LearningVuFind.pdf
