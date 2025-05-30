# BAIN FS25 - Suchmaschinen und Discovery-Systeme II





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
2. Droplets erstellen auf Basis dieses Images
3. Passwörter vergeben

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

1. Laden der Beispieldaten (MARC21) aus https://github.com/Rouven-Schabinger/bain-jupyter-codespaces (example und output)

```shell
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/example/alma-marc21.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/example/openrefine-doaj-marc21.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/output/archivesspace-ead_transformed.xml
wget https://raw.githubusercontent.com/Rouven-Schabinger/bain-jupyter-codespaces/refs/heads/main/output/dspace-oai-dc_transformed.xml
```


2. Vor dem Import die Datei `marc_local.properties` bearbeiten um den Daten eine "Institution" und eine "Bibliothek" zuzuweisen.

```shell
nano /usr/local/vufind/import/marc_local.properties
```

3. Importscript für die erste Datenquelle starten. Beispiel für Alma:

```shell
/usr/local/vufind/import-marc.sh alma-marc21.xml
```

4. Schritte 2 und 3 für die übrigen Datenquellen wiederholen.
* Achtung: Der Import der Beispieldaten von ArchivesSpace und DSpace schlägt fehl. Finden Sie die Ursache.

### Ergebnisse / Rückfragen


* 




## Gruppenarbeit VuFind-Konfiguration
* https://vufind.org/wiki/configuration
* https://github.com/vufind-org/learning-vufind-book 
* Das globale Konfigurationsverzeichnis befindet sich unter dem Pfad /usr/local/vufind/config/vufind
* Das lokale Konfigurationsverzeichnis befindet sich unter dem Pfad /usr/local/vufind/local/config/vufind

config.ini
https://vufind.felixlohmeier.de/#/06_Konfiguration_Allgemein

evtl. noch facets.ini
https://vufind.felixlohmeier.de/#/08_Konfiguration_Facetten

**Aufgabe**
* Ändern Sie einige Einstellungen z.B. Theme oder Facetten nach links
* Kopieren Sie wenn nicht vorhanden die config.ini und facets.ini vom globalen Verzeichnis in das lokale

### Ergebnisse / Rückfragen

Gruppe 1:

* 

Gruppe 2:

* 

Gruppe 3:
* ...

**Videos**: https://www.youtube.com/watch?v=XVSktvVM4d0&list=PL5_8_wT3JpgE5rv38PwE2ulKlgzBY389y


## Schweiz: SLSP

* Durch [Swiss Library Service Platform](https://slsp.ch) wurde Ex Libris Alma und damit auch das dazu gehörige Discovery-System **Primo VE** und dem CDI (mehr als 3 Milliarden elektronische Artikel ) an den wissenschaftlichen Bibliotheken in der Schweiz eingeführt.
* Am Mo, 7.12.2020 ist das Rechercheportal [swisscovery](https://swisscovery.slsp.ch) gestartet.
* Was ist drin?

 ![image](https://hackmd.io/_uploads/BJl4h5s_1x.png)
 
* Externe Quellen:
![image](https://hackmd.io/_uploads/SybXJisO1x.png)
werden geharvested (OAI) und normalisiert
* Systemarchitektur
* Herausforderungen:
    * Monatliche Releases durch System-Provider, z.B.https://knowledge.exlibrisgroup.com/Primo/Release_Notes/002Primo_VE/2025/010Primo_VE_2025_Release_Notes?mon=All
    * Ausarbeitung der Discovery-Services​
    * Laufend Änderungen in allen Funktionsbereichen von Alma
    * Bugs​
    * Unterschiedliche Bedürfnisse der Bibliotheken
* Konfiguration einer View: 3 Ebenen​
    * View-Ebene (z.B. http://bsb.swisscovery.slsp.ch/discovery/search?vid=41SLSP_RBE:StASO)
    * Institutions-Ebene (z.B. https://bsb.swisscovery.slsp.ch/discovery/search?vid=41SLSP_RBE:VU1)
    * Zentral auf Netzwerk-Ebene (swisscovery)
    * Bei UI-Customization mehrere Modelle: Zentrales Package oder nicht: https://github.com/Swiss-Library-Service-Platform/central-customization-package
        * Pflege durch eine Gruppe von Entwickler:innen Agile Project for Customization (APC)




### Primo VE Anzeige
Volltitelanzeige: in swisscovery festgelegter SLSP-Standard​

Anzeige-Felder (Out of the box „Display Fields“) und personalisierte Anzeige-Felder („Local Fields“)​

* Out-of-the-box Mapping der Dublin Core MARC21-Felder in die Anzeige-Felder: [Mapping to the Display, Facets, and Search Sections in the Primo VE Record](https://knowledge.exlibrisgroup.com/Primo/Product_Documentation/020Primo_VE/Primo_VE_(English)/120Other_Configurations/Mapping_to_the_Display%2C_Facets%2C_and_Search_Sections_in_the_Primo_VE_Record)

* Angepasstes Mapping via “Local Fields”, z.B. für die 5XX-er-Felder ​
* Ziel: Transformation der Quelldaten ins Zielformat «PNX» (Primo Normalized XML)

* Informationen sind über das PNX zu sehen, siehe Bsp. Hinzufügen von &showPnx=true in der URL

Bsp.:

* Dublin Core: https://zhdk.swisscovery.org/discovery/sourceRecord?vid=41SLSP_ZHK:ZHDK&docId=alma99123942763105512&recordOwner=41SLSP_ZHK
* PNX: https://zhdk.swisscovery.org/discovery/fulldisplay?docid=alma99123942763105512&context=L&vid=41SLSP_ZHK:ZHDK&lang=de&search_scope=DN_and_CI&adaptor=Local%20Search%20Engine&tab=41SLSP_ZHK_DN_CI&query=any,contains,safavid%20heritage%20occasion&offset=0&showPnx=true
* Nutzeransicht: https://zhdk.swisscovery.org/permalink/41SLSP_ZHK/1ub1o07/alma99123942763105512

## Exkurs Browser Developer Tools ##

Die Browser Developer Tools sind Werkzeuge in modernen Webbrowsern, die Entwicklern helfen, Webseiten zu analysieren und zu optimieren. 
Hauptfunktionen:

* Element-Inspektor: Untersucht und bearbeitet HTML und CSS direkt im Browser.
* Konsole: Debuggt JavaScript und führt Befehle aus.
* Netzwerk-Analyse: Überwacht die Ladezeiten und Fehler von Ressourcen.
* Performance-Analyse: Analysiert die Ladegeschwindigkeit der Webseite.
* Speicher-Analyse: Überwacht den Speicherverbrauch und identifiziert Lecks.

**Übung [optional]**
* versuchen Sie live mit den developer tools im Browser die *Quelldaten* auszublenden:
 ![image](https://hackmd.io/_uploads/S1bEQDJgel.png)
* `<span translate="fulldisplay.sourcerecord">Quelldaten</span>`
* Suchen Sie im Internet nach einer Lösung

**Zukunft Primo VE**

https://knowledge.exlibrisgroup.com/Primo/Product_Materials/001_Next_Discovery_Experience_(NDE)/Next_Discovery_Experience_User_Interface


## Marktüberblick Discovery-Systeme

### Eigenschaften von Discovery-Systemen
* Externe Quellen 
* Echte Suchmaschine​
* Suche in natürlicher Sprache möglich​
* Usability ​
* Zahlreiche Services drumherum: auch Delivery (Online, Digitalisierung usw.)



### Systeme International (kommerziell)

* Jährlicher Library Systems Report von Marshall Breeding im ALA Magazine: <https://americanlibrariesmagazine.org/2025/05/01/2025-library-systems-report/>
    * [Suche auf librarytechnology.org](https://librarytechnology.org/products/main.pl) vermittelt guten Überblick
    * siehe auch [Statistik der Verkaufszahlen](https://librarytechnology.org/products/sales/)

#### Übung
* Identifizieren und analysieren Sie die wichtigsten Trends auf dem Markt für Bibliothekstechnologie mit Fokus auf Discovery, wie sie im Bericht beschrieben sind. Diskutieren Sie, wie sich diese Trends auf die Zukunft der Bibliotheksdienste auswirken könnten.

*Leitfragen:
Was sind die wichtigsten Trends in der Bibliothekstechnologie?
Wie wirken sich diese Trends auf verschiedene Arten von Bibliotheken (öffentliche, akademische, Schul-, Spezialbibliotheken) aus?
Was sind die potenziellen Vorteile und Herausforderungen dieser Trends?*
* ist der Report allgemeingültig oder fehlt etwas?

###  --------

* Marktführer ist Ex Libris mit [Primo / VE] und dem Central Discovery Index (CDI): https://exlibrisgroup.com/products/primo-discovery-service/content-index/
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

* Open Source-Alternative: [VuFind](https://vufind.org/vufind/) (ohne eigenen Artikelindex) oder [Blacklight](https://projectblacklight.org/), https://doi.org/10.29085/9781783301409.010 
* Alternative Zentralindizes aus dem deutschsprachigen Raum: [K10plus-Zentral](https://verbundwiki.gbv.de/display/VZG/K10plus-Zentral), [finc Artikelindex](https://finc.info/services)


### Exkurs: Swisscollections 

> Developed by [University Library of Basel](https://ub.unibas.ch/) in collaboration with [arbim IT ](https://arbim.ch/)and [outermedia](https://www.outermedia.de/)
* Vom Verein swisscollections wird der Sucheinstieg [swisscollections](https://swisscollections.ch) für Sammlungen angeboten. Dieses Portal wurde mit VuFind und Eigenentwicklungen der UB Basel realisiert.
* https://gitlab.switch.ch/swissbib/swisscollections
* [Präsentation](https://libreabc.ch/wp-content/uploads/2023/09/Walter-swisscollections-LibreABC2023.pdf) und https://vufind.org/docs/summit2021/walter-bohm.pdf
* https://ub-basel.atlassian.net/wiki/spaces/swisscollections/overview?homepageId=1974272247
* https://www.youtube.com/watch?v=nN67VwmXLDI
* https://de.wikipedia.org/wiki/Swisscollections



### Sonstiges


* Selbstgebastelte Metasuche (Bento-Box):
    * Lib4RI: https://www.lib4ri.ch/search-tool
    * https://codeberg.org/Lib4RI/Lib4RI-Search-Tool

* Portal: recherche-patrimoniale.ch

* Dauerthema: UX / Usability und Analytics (Bsp. FHGR Studie)

### Literaturasuwahl

* Renke Siems: Das Leben der Anderen
https://doi.org/10.5282/o-bib/5797
* Christensen, Anne, and Matthias Finck. 2021. ‘Discovery-Systeme: Eine Analyse ihrer Geschichte und Gegenwart mit dem Hype-Zyklus’. Bibliothek Forschung und Praxis 45 (3): 497–508. https://doi.org/10.1515/bfp-2021-0039.  
* Nishikawa-Pacher, Andreas. 2023. ‘A typology of research discovery tools’. Journal of Information Science, 49(4), 1086–1095. https://doi.org/10.1177/01655515211040654. 
* Nishikawa-Pacher, Andreas. 2023. ‘A typology of research discovery tools’. Journal of Information Science, 49(4), 1086–1095. https://doi.org/10.1177/01655515211040654. 
* Balnaves, E., Bultrini, L., Cox, A. M., & Uzwyshyn, R. (2025). New horizons in artificial intelligence in libraries. De Gruyter Saur. https://doi.org/10.1515/9783111336435 

 * Bibliomaps: Books location in libraries. (n.d.). Retrieved 4 May 2023, from https://bibliomaps.es/  

* BibTip. (n.d.). Retrieved 4 May 2023, from https://www.bibtip.de/de 
* Open Knowledge Maps: A visual interface to the world’s scientific knowledge. (n.d.). Open Knowledge Maps. Retrieved 4 May 2023, from https://openknowledgemaps.org/   


## Organisatorisches

* **Lehrevaluation**

jetzt oder spätestens bis 30. Mai ausfüllen, damit wir es in der letzen Stunde besprechen können
