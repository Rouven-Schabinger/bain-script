---
title: BAIN FS25 - Suchmaschinen und Discovery-Systeme | Import

---

# BAIN FS25 - Suchmaschinen und Discovery-Systeme | Import



## Lerntagebücher

* Vorgaben in der [Semesterinformation in Moodle](https://moodle.fhgr.ch/mod/page/view.php?id=785802)
* Fragen zu Form oder Bewertungskriterien?
  * Fragen können gerne auch später noch per im Diskussion-Forum oder per E-Mail gestellt werden: rouven.schabinger@fhgr.ch
* Abgabe am 04. Juli per E-Mail an rouven.schabinger@fhgr.ch

## Gruppenarbeit Datenintegration

Ziel: Import aller Daten in VuFind

![mermaid-2025-01-16-144111](https://hackmd.io/_uploads/Sk7h5c8wyl.png)

## Einteilung Gruppen

Gruppe 1
* Server: X.X.X.X
* VuFind: http://X.X.X.X/vufind
* Passwort: a1U8c7xb
* Teilnehmer*innen:
  * 
  * 
  * 
  * 

Gruppe 2
* Server: X.X.X.X
* VuFind: http://X.X.X.X/vufind
* Passwort: a2U8c7xb
* Teilnehmer*innen:
  * 
  * 
  * 

Gruppe 3
* Server: X.X.X.X
* VuFind: http://X.X.X.X/vufind
* Passwort: a3U8c7xb
* Teilnehmer*innen:
  * 
  *  
  * 

## Vorbereitung Gruppenarbeit

1. Server klonen via Live-Snapshot
2. Login mit Webkonsole und Solr starten:
```
/usr/local/vufind/solr.sh -force start
```

## SSH Zugriff

Eine Person pro Gruppe bzw. Server 

Linux/MacOS: Terminal
Windows: Powershell

```
ssh root@x.x.x.x
```

### Testdaten löschen

Quelle: https://vufind.org/wiki/indexing:re-indexing

```shell
/usr/local/vufind/solr.sh stop
rm -rf /usr/local/vufind/solr/vufind/biblio/index /usr/local/vufind/solr/vufind/biblio/spell*
/usr/local/vufind/solr.sh -force start
```

### Daten importieren

1. Laden der Beispieldaten aus https://github.com/Rouven-Schabinger/bain-jupyter-codespaces (example und output)

```shell
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/example/alma-marc21.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/example/openrefine-doaj-marc21.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/output/archivesspace-ead_transformed.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/example/dspace-oai-dc.xml
```


2. Vor dem Import die Datei `marc_local.properties` bearbeiten um den Daten eine "Institution" zuzuweisen.

```shell
nano /usr/local/vufind/import/marc_local.properties
```

3. Importscript für die erste Datenquelle starten. Beispiel für Koha:

```shell
/usr/local/vufind/import-marc.sh koha-marc21.xml
```

4. Schritte 2 und 3 für die übrigen Datenquellen wiederholen.
* Achtung: Der Import der Beispieldaten von ArchivesSpace und DSpace schlägt fehl. Finden Sie die Ursache.

### Ergebnisse / Rückfragen



* Fehlermeldung bei ArchivesSpace Dspace: 
![](https://pad.gwdg.de/uploads/efbb98d9-59fe-4355-8570-0ff7364083b4.png)
-> könnte man lösen, indem man ein zusätzliches Feld in den Metadaten mit der ID hinzufügt?



## Gruppenarbeit VuFind-Konfiguration
* https://vufind.org/wiki/configuration
* https://github.com/vufind-org/learning-vufind-book 
* Das globale Konfigurationsverzeichnis befindet sich unter dem Pfad /usr/local/vufind/config/vufind
* Das lokale Konfigurationsverzeichnis befindet sich unter dem Pfad /usr/local/vufind/local/config/vufind

config.ini
https://vufind.felixlohmeier.de/#/06_Konfiguration_Allgemein

evtl. noch facets.ini
https://vufind.felixlohmeier.de/#/08_Konfiguration_Facetten

### Ergebnisse / Rückfragen

Gruppe 1:
* sidebarOnLeft = true -> zeigt diese links an (siehe Ansicht 1)
![](https://pad.gwdg.de/uploads/34acc425-43fc-4c46-a7ee-b43a956ab768.png)

* Design geändert (siehe Ansicht 1)
![](https://pad.gwdg.de/uploads/fc9d207b-eddf-4127-aaa2-263f463b5058.png)
*  Ansicht 1
![](https://pad.gwdg.de/uploads/81fac57a-2ad0-4fed-a09f-e6ae8c16f801.png)
* Ansicht 2: Bilder rechts
![](https://pad.gwdg.de/uploads/ae8018cb-4231-4fa6-8747-96c61fed4f39.png)
* Tab-Titel und Seperator geändert
![](https://pad.gwdg.de/uploads/db3d7500-483c-4a89-8df0-3060920ff3d1.png)
![](https://pad.gwdg.de/uploads/179a4396-69f5-49a5-95e2-b6ed69f7e90f.png)




Gruppe 2:

Facetten:
- ![](https://pad.gwdg.de/uploads/9768ba5e-013d-4681-bf04-ca607c18e508.png)
collection = Collection
![](https://pad.gwdg.de/uploads/9d17db13-8247-4923-a0de-4dc6a150cea7.png)
- Facettenwerte bei "Sprache" werden nicht nach eingestellter Sprache übersetzt. 
![](https://pad.gwdg.de/uploads/454d477f-9604-4fbf-ae2e-c63bd5491aa0.png)

- ; callnumber-first = "Call Number" wurde deaktiviert, weil wir Signatur nicht brauchen


Configuration: 
- theme = sandal
    ![](https://pad.gwdg.de/uploads/5c8ac4a9-732c-4091-a018-6099a7b171f7.png)
- title geändert
    ![](https://pad.gwdg.de/uploads/6506aa23-e298-45d4-a490-1134c5f989a9.png)
    



Gruppe 3:
* ...



## Marktüberblick Discovery-Systeme

### Eigenschaften von Discovery-Systemen
* Externe Quellen 
* Echte Suchmaschine​
* Suche in natürlicher Sprache möglich​
* Usability ​
* Zahlreiche Services drumherum: auch Delivery (Online, Digitalisierung usw.)

## Exkurs: Ranking-Kriterien (Bsp. Primo)
* Grad der Übereinstimmung zwischen Suchanfrage und Informationen in Datensatz (tf-idf-Bewertungsmodell*)​
    * Term Frequency + Inverse Document Frequency​
* Wissenschaftliche Bedeutung einer Ressource (z.B. Publikation in peer-reviewed Journal)​
* Relevanz einer Ressource hinsichtlich des Typs der Suchanfrage (z.B. known-item search oder broad-topic search)​
* Erscheinungsdatum einer Ressource​

Frage: Unbehagen bezüglich der Sortierung der Treffer?

Indexierung: [Clarivate  Overview of the Index and Search Process ](https://knowledge.exlibrisgroup.com/Primo/Product_Documentation/Primo/System_Administration_Guide/010System_Architecture/050Overview_of_the_Index_and_Search_Process)


### International (kommerziell)

* Jährlicher Library Systems Report von Marshall Breeding im ALA Magazine: <https://americanlibrariesmagazine.org/2024/05/01/2024-library-systems-report/>
    * [Suche auf librarytechnology.org](https://librarytechnology.org/products/main.pl) vermittelt guten Überblick
    * siehe auch [Statistik der Verkaufszahlen](https://librarytechnology.org/products/sales/)
* Marktführer ist Ex Libris mit [Primo] und dem Central Discovery Index: (https://exlibrisgroup.com/products/primo-discovery-service/content-index/)
    * Alternative: OCLC mit [WorldCat Discovery](https://www.oclc.org/de/worldcat-discovery.html), z.B. https://ufz.on.worldcat.org/discovery
    * Alternative: EBSCO mit [EDS](https://www.ebsco.com/de-de/wissenschaftliche-bibliotheken/produkte/ebsco-discovery-service), z.B: https://katalog.ub.uni-freiburg.de/opac
    * (Summon wird zugunsten von Primo abgekündigt)
    * (Google Scholar usw.)

![image](https://hackmd.io/_uploads/r1wi5qiuJx.png)
https://librarytechnology.org/vendor/exlibris​

Gefahr von **Fusionen**: 
* Ein einziges Paket für alles​
* Neutralität der Inhalte​
* Dominante Stellung bestimmter Akteure​
* Beschränkte Konkurrenz und hohe Preise

Note:
- Den Library Systems Report hatten wir uns zuvor bereits angeschaut, damals jedoch mit Blick auf Bibliothekssysteme. Marshall Breeding führt in seinem Bericht aber auch Discovery-Systeme auf.
- Die Funktionalität eines Discovery-Systems besteht aus mindestens zwei Komponenten: Der Software und den Daten.
- Kommerzielle Discovery-Systeme verkaufen einen Suchindex meist separat, der vor allem Metadaten zu elektronischen Artikeln enthält.

### International (Open Source)

* Open Source-Alternative: [VuFind](https://vufind.org/vufind/) (ohne eigenen Artikelindex)
    * Nische: [typo3-find](https://github.com/subugoe/typo3-find)
* Alternative Zentralindizes: [K10plus-Zentral](https://verbundwiki.gbv.de/display/VZG/K10plus-Zentral), [finc Artikelindex](https://finc.info/services)

### Schweiz: SLSP

* Durch [Swiss Library Service Platform](https://slsp.ch) wurde Ex Libris Alma und damit auch das dazu gehörige Discovery-System Primo VE an den wissenschaftlichen Bibliotheken in der Schweiz eingeführt.
* Am Mo, 7.12.2020 ist das Rechercheportal [swisscovery](https://swisscovery.slsp.ch) gestartet.
* Zentrale User Datenbank und Anmeldung via https://eduid.ch/ (Switch)
Literatur: https://it-in-bibliotheken.de/sicherheit.html#pr%C3%A4ventivma%C3%9Fnahmen 5.4.2 Authentifizierung und Autorisierung
* Was ist drin?

 ![image](https://hackmd.io/_uploads/BJl4h5s_1x.png)
 
* Externe Quellen:
![image](https://hackmd.io/_uploads/SybXJisO1x.png)
werden geharvested (OAI) und normalisiert
* Systemarchitektur

* Ergänzend zu SLSP wird vom Verein swisscollections der Sucheinstieg [swisscollections](https://swisscollections.ch) für Sammlungen angeboten. Dieses Portal wurde mit VuFind und Eigenentwicklungen der UB Basel realisiert.

* Selbstgebastelte Metasuche (Bento-Box):
    * Lib4RI: https://www.lib4ri.ch/search-tool
    * https://codeberg.org/Lib4RI/Lib4RI-Search-Tool

* Dauerthema: UX / Usability

### Literaturtipp zu User Tracking

Renke Siems: Das Leben der Anderen
https://doi.org/10.5282/o-bib/5797