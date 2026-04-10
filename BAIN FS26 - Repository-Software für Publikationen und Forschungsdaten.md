# BAIN FS26 - Repository-Software für Publikationen und Forschungsdaten

## Lerntagebücher Zwischenabgabe

* generell eher gute und unikate Abgaben!

Allgemeine Hinweise:
*	**Abkürzungen** auflösen, wenn nicht in Vorlesung behandelt
*	**Bilder/Grafiken** können Zusatzpunke bingen, müssen aber Eigenwert haben neben Ästhetik und lesbar sein
*	Zeichenanzahl erfordert **Präzision**: wohldosierter Fremdbezug, “Allgemeines”/"GPT Lingo"  knapp halten 
*	**Fluglevel**: Grosse Reflexionen ans Ende. Im Kapitel möglichst wechseln zwischen Theorie und Praxis: verankern mit konkreten Übungseinblicken 
*	**Blumige Begriffe** für Inhaltswiedergabe eher vermeiden, weil Interpretation offen
*	**Quellen** einbeziehen, falls kein beruflicher Kontext vorhanden, Bezug zu anderen Modulen gut
*	**Roter Faden**, kein Vorgangsprotokoll: wir haben das behandelt, dann haben wir das behandelt ... 	
*	**PDF** keine DOCX
*	Alle Kapitel müssen da sein, ganze Sätze schreiben und **Zeichenanzahl** einhalten
*	Stellen Sie sich vor Sie wären in meiner Position / Wie würden Sie sich selbst bewerten = **Glaubhaftigkeit**



## Rückblick

* Quiz zu Archivsystemen



## Open Access und Open Data

* Was ist ein Repositorium? Welche kennen Sie?



- [Zenodo](https://zenodo.org) (InvenioRDM), vgl. https://github.com/zenodo/zenodo
    - Upgrade-Probleme: https://blog.zenodo.org/2023/10/19/2023-10-19-upgrade-issues/

- **Publikationen**
  - Open Access, vgl. https://consortium.ch/

```
Das Konsortium der Schweizer Hochschulbibliotheken erwirbt Lizenzen
für wissenschaftliche Ressourcen (elektronische Zeitschriften, 
E-Books und Datenbanken). Es bietet ein breites Dienstleistungsspektrum 
an und unterstützt die Bestrebungen nach einer nationalen 
Open-Access-Strategie. Es trägt damit massgeblich zur 
Sicherung der Qualität und Wettbewerbsfähigkeit des 
Hochschul- und Forschungsplatzes Schweiz bei. 
Die Geschäftsstelle des Konsortiums wird von SLSP geführt.
```


- [Swiss Open Access Monitor](https://oamonitor.ch/de/)
- [Statistik zu Open-Access-Repositorien via COAR](https://ird.coar-repositories.org )
 
 Sonst gibt es noch https://opendoar.ac.uk oder https://roar.eprints.org/view/type/ als Übersicht
  - früher Vertreter:arXiv-Server für Physik-Preprints : https://arxiv.org/
  - Fokus bei vilen: Zweitveröffentlichungen ("grüner Weg") und Hochschulschriften

FYI:
-  Zweitveröffentlichungsrecht in der Schweiz: https://www.uzh.ch/blog/ub/2023/05/31/das-projekt-zweitveroeffentlichungsrecht-und-open-access-als-regulatorische-herausforderung-hintergrund-und-projektziele/


Aktuelles zu Schweizer Repositorien:
* [ NAIF - 
National Approach for Interoperable repositories
and Findable research results
](https://eth-library.github.io/naif/) Slides: dx.doi.org/10.5281/zenodo.18633494
* [SOAD - Swiss Open Academic Data](https://soad.ch/) nicht [SOAD](https://en.wikipedia.org/wiki/System_of_a_Down)
* [Recommendations for Swiss
Higher Education Institutions
to enhance the visibility of their
research output](https://www.research-collection.ethz.ch/server/api/core/bitstreams/097f017a-1d8c-439c-97b7-62281392028a/content)

- **Forschungsdaten**
  - Open Data
  - Transparenz und Repoduzierbarkeit [Open Science](https://en.wikipedia.org/wiki/Open_science)
  - [Verzeichnis von Forschungsdaten-Repositorien](https://www.re3data.org)
      - Länder, Typen, Communities, Langzeitarchivierung, PID, Forschungssoftware
      - Schema: https://www.re3data.org/schema
      - RESTful API/Jupyter Notebook: https://coref.project.re3data.org/blog/using_the_re3data_api
  - Fokus: Primärdaten, die bei der Forschung entstehen. Oft Daten als Anhang zu Zeitschriftenartikeln, aber auch auch als eigenständige Publikation möglich


  --> wichtiges Arbeitsfeld für Infrastrukturanbieter in der Hochschullandschaft (z.B. Bibliotheken)


- Bsp. Verknüpfung Forschungsdatum und Publikation via DataCite Metadata Schema:

 R. Schabinger. (2023). Does size matter? Quality assessment of the size property in research data repositories [Data set]. Zenodo.  [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.7643637.svg)](https://doi.org/10.5281/zenodo.7643637)

```
"related_identifiers": [
      {
        "identifier": "10.5281/zenodo.8192783",
        "relation_type": {
          "id": "issupplementto",
          "title": {
            "de": "Erg\u00e4nzt",
            "en": "Is supplement to"
          }
        },
        "resource_type": {
          "id": "publication-thesis",
          "title": {
            "de": "Abschlussarbeit",
            "en": "Thesis"
          }
        },
        "scheme": "doi"
      }
    ]
```



### Übung ###
- Suchen Sie in der GUI von re3data nach Schweizer Repositorien, welche eine restriktiven Datenupload haben und DOI unterstützen
- Machen Sie sich mit dem Schema (2.2) vertraut, gibt es eine property zum "Umfang" des Repositoriums, wie ist sie definiert?
- Starten Sie Ihren Github Code Space als Jupyter: https://github.com/Rouven-Schabinger/bain-re3data
- ![image](https://hackmd.io/_uploads/r1MDDCGhJx.png)
- Passen Sie das vorgeführte Jupyter Notebook an: https://github.com/Rouven-Schabinger/bain-re3data/blob/main/examples-python/01_re3data_API_medical_research_community.ipynb
    - lesen sie die Kommentare / Dokumentation
    - der query soll ihrere Suche in der GUI entsprechen
    - extrahieren Sie zusätzlich noch den "Umfang" des Repositoriums


#### Erkenntnisse / Fragen ####
*

### Forschungsinformationen

- Informationen über Forschende, Drittmittelprojekte, Patente und vieles mehr.
- Ziel ist die Forschungsberichterstattung. Um die Daten zusammenzuführen und Berichte erstellen zu können, werden oft Forschungsinformationssysteme an den Universitäten eingeführt.
- Beispiel: ["Kerndatensatz Forschung" in Deutschland](https://kerndatensatz-forschung.de/version1/technisches_datenmodell/v_1_3/ER-Modell.html)
- Zum Stand in der Schweiz: Ackermann Krzemnicki, Sonia and Hägele, Bernd F. (2016): Die Standardisierung von Forschungsinformationen an Schweizer universitären Hochschulen. https://edoc.unibas.ch/54788/


- Beispiel: [PHSG Proforis](https://proforis.phsg.ch/home) (DSpace-CRIS)



 **Government Data** oder **OER** (Open Educational Resources)
    - https://opendata.swiss/de
    - https://oer-repository.switch.ch/edu-sharing/components/search?q=


Konvergenz:
  - als Plattform: https://opendatanavigator.switch.ch/
  - Als Modell: https://datacite.org/blog/introducing-the-pid-graph/ DataCite
  - als Daten: collections as data z.B. https://collada.ethz.ch 

Sonstiges:
- Slides zu PIDs Bsp ARK: https://docs.google.com/presentation/d/1XEpGwON6yzD357GlUkskB1T9MGTvO_XCkuSHtxT3Pxg/edit?slide=id.g21a3fb692a4_0_46#slide=id.g21a3fb692a4_0_46


## Übungen mit DSpace

Standardfragen IT:

- Make or Buy
    - Service Providers: https://dspace.org/registered-service-providers/
- Authentifizierung (z.b Edu-ID, ORCID), Rollen und Rechte
    - vgl. https://help.switch.ch/aai/
    - https://it-in-bibliotheken.de/sicherheit.html#authentifizierung-und-autorisierung

### Einführung in DSpace

- Software geeignet für Publikationen und Forschungsdaten, Features: https://dspace.org/features/
- seit 25 Jahren genutzt von 3000 Institutionen (https://dspace.org/wp-content/uploads/2025/12/AR-2024-25-DSpace.pdf)
- Metadatenstandard: Qualified Dublin Core, kann aber auch mit [DataCite](https://schema.datacite.org/) (Exkurs?) Metadatenschema betrieben werden.
- DSpace 6: 2016 erstmalig veröffentlicht , wird nicht mehr weiterentwickelt und der [Support endete am 1.7.2023](https://wiki.lyrasis.org/display/DSPACE/Support+for+DSpace+5+and+6+is+ending+in+2023)
- DSpace 7: 2021 veröffentlicht, neue Technologien im Frontend (Angular) und Backend (neue REST API)
- DSpace 8: 2024: generelle Verbesserungen
- DSpace 9: 2025

![Picture1](https://hackmd.io/_uploads/rktyqwI3-l.png)
- DSpace 10: (in Planung)
Merger mit DSpace-CRIS (Erweiterung für Forschungsinformationen)



DSpace hat eine 3-Schichten-**Architektur**: 
- Anwendungsschicht (Application Layer)
    die Anwendungsschicht umfasst die Komponenten, mit denen eine DSpace-Instanz mit der Außenwelt kommuniziert, zum Beispiel Webschnittstelle, OAI-PMH-Schnittstelle.
- Geschäftslogik (Business Logic Layer)
    diese Schicht verwaltet Inhalt, Benutzer und Gruppen, Rechte und Geschäftsgänge.
 - Speicherung (Storage Layer)
    diese Schicht kümmert sich um die physikalische Speicherung von Metadaten und Inhalt.
    
 https://de.wikipedia.org/wiki/DSpace_(Software)


### DSpace Demo

Aus Zeitgründen keine Installation, nur Test mit öffentlich zugänglicher Demo.

DSpace Demo: https://demo.dspace.org

Wird laufend aktualisiert

- Site Administrator: `dspacedemo+admin@gmail.com`
- Community Administrator: `dspacedemo+commadmin@gmail.com`
- Collection Administrator: `dspacedemo+colladmin@gmail.com`
- Submitter: `dspacedemo+submit@gmail.com`
- Passwort immer: `dspace`

Manual: https://wiki.lyrasis.org/display/DSDOC9x/Learning+DSpace 

### Übung: Communities und Collections

Machen Sie sich mit der graphischen Oberfläche vertraut.

- Aufgabe 1: Erstellen Sie eine Community (Bereich), erstellen Sie eine Rolle und fügen Sie Berechtigungen für den "Community Administrator" hinzu. 
  - Login: `dspacedemo+admin@gmail.com`
  - Passwort: `dspace`
- Aufgabe 2: Erstellen Sie eine Collection (Sammlung), erstellen Sie eine Rolle und fügen Sie Berechtigungen für den "Collection Administrator" hinzu.
  - Login: `dspacedemo+commadmin@gmail.com`
  - Passwort: `dspace`
- Ziel: Dokumentieren Sie den Link zu Ihrer Collection unten im gemeinsamen Dokument.

Links zu Collections:


Hinweise:
- Der Grund, warum es zusätzlich zu Collections auch noch Communities gibt, ist das Rechtemanagement. In der Community wird festgelegt wer die (ggf. mehrere zugehörige) Collections verwalten darf. Das möchte man nur an einer Stelle und nicht an jeder Collection definieren. Außerdem können ganze Communities "geharvestet" werden, also Daten einer Einrichtung über die Schnittstellen abgefragt werden.

### Fragen / Erkenntnisse
* 

### Einreichung und Review

DSpace Demo: https://demo.dspace.org

* Um Rechteprobleme zu vermeiden, Login mit DSpace-Admin
* MyDspace bei Login-Button aufrufen
* Neues Dokument anlegen (z.B. "Veröffentlichung"), Datei hochladen. Sammlung: 1-step-workflow
* In MyDSpace auf "Zeige Workflow Aufgaben" wechseln. Dort werden Dokumente zur Bearbeitung/Freigabe aufgeführt
* Bsp. DOI workflow (ETH Zurich DOI Desk): https://ethz.ch/content/dam/ethz/associates/ethlibrary-dam/documents/Publizieren-und-Archivieren/A-step-to-step-guide-to-DOI-registration.pdf 

### Import und Export

- DSpace bietet auch dateibasierten Import, besonders relevant sind im Kontext von Repositorien aber die Schnittstellen:
  - SWORD ermöglicht die Publikation in DSpace (Metadaten und Datei-Upload) von einer anderen Webseite aus (z.B. Intranet der Hochschule).
  - OAI-PMH ermöglicht es externen Systemen die in DSpace verzeichneten Metadaten abzurufen.
- OAI-PMH-Schnittstelle der DSpace-Demo (Daten erscheinen dort zeitverzögert): http://demo.dspace.org/oai/request?verb=ListSets
- Beispiel für Portal auf Basis von OAI-PMH: Die [Bielefeld Academic Search Engine (BASE)](https://www.base-search.net/) "erntet" weltweit OAI-PMH-Schnittstellen und verzeichnet damit weit über 250 Mio. Dokumente.

Note:

* [SWORD](https://en.wikipedia.org/wiki/SWORD_(protocol)) ist eine Schnittstelle, um Publikationen in einem Repository abzuliefern. Damit kann ein Formular mit Dateiupload auf einer Webseite (außerhalb der Repository-Webseite) angeboten werden.
* Um Daten aus dem Repository auf Webseiten anzuzeigen, z.B. eine Publikationsliste, werden andere Schnittstellen wie [RSS-Feeds](https://de.wikipedia.org/wiki/RSS_(Web-Feed)) verwendet

### Übung: Massenänderung von Metadaten

-  Massenänderung von Metadaten
https://wiki.lyrasis.org/display/DSDOC9x/Batch+Metadata+Editing
- Exportieren Sie die Metadaten einer Collection in BAIN, es sollte mindestens ein record enthalten sein
Korrigieren sie etwas im Titel des records, z.B. in einem Textverarbeitungsprogramm
Importieren sie die Metadaten und prüfen Sie die Änderung
ting
- Exportieren Sie die Metadaten einer Collection in BAIN, es sollte mindestens ein record enthalten sein
- Korrigieren sie etwas im Titel des records, z.B. in einem Textverarbeitungsprogramm
- Importieren sie die Metadaten und prüfen Sie die Änderung
- Optional: wie kann man Werte löschen?

### Literatur zu DSpace

- Präsentationsfolien und Videomitschnitte der Präsentationen auf den jährlichen D/A/CH-Anwendertreffen: https://wiki.lyrasis.org/display/DSPACE/DSpace+Praxistreffen+2026
- Suchmaschinenoptimierung (SEO): [Abschnitt im Nutzerhandbuch von DSpace zu SEO](https://wiki.lyrasis.org/display/DSDOC8x/Search+Engine+Optimization)

### FHGR Repositorium
- https://repository.fhgr.ch/
- [Infos](https://my.fhgr.ch/index.php?id=home&tx_fhgrnews_news%5bidNews%5d=6349&tx_fhgrnews_news%5baction%5d=show&tx_fhgrnews_news%5bcontroller%5d=News&tx_fhgrnews_news%5bsource%5d=mail)

Hintergründe zur Einführung:

- https://drive.google.com/file/d/1KSLr3v47NZphght2DqPQm04EitJ-aZzL/view?usp=sharing

## Marktüberblick Repository-Software

- Grundsätzliches zu Repositorien: https://open-access.network/informieren/publizieren/repositorien
- Open Directory of Open Access Repositories (OpenDOAR): https://v2.sherpa.ac.uk/view/repository_by_country/Switzerland.html
- Instanzen in der Schweiz: https://forschungsdaten.info/fdm-im-deutschsprachigen-raum/schweiz/rdm-infrastructure-repositories/repositories/

### Relevante Systeme in D/A/CH


- [DSpace](https://www.dspace.org)
- [EPrints](https://www.eprints.org)
- [Fedora](http://fedorarepository.org) / [Islandora](https://islandora.ca) (wird auch benutzt bei docuteam box)
- [InvenioRDM](https://invenio-software.org/products/rdm/)
  - besonders interessant, weil seit Oktober 2023 die Basis von Zenodo am CERN
- [MyCoRe](https://www.mycore.de)
- [OPUS](https://www.opus-repository.org)
- [Alma digital](https://knowledge.exlibrisgroup.com/Alma/Training/Alma_Digital/01_Alma_Digital%3A_Overview): und bald: [Specto](https://www.meetspecto.com/)
    - z.B. https://www.alexandria.ch/discovery/collectionDiscovery?vid=41BIG_INST:ALEX&lang=de

![image](https://hackmd.io/_uploads/S1n0FRfnJl.png)

- FHGR?
- Wechsel eines Repositoriums: https://journal.code4lib.org/articles/17398
  - gerade war Code4Lib Conference: https://2026.code4lib.org/


### Langzeitarchivierung

Für digitale Langzeitarchivierung (digital preservation, digital asset management) oft noch zusätzliche Systeme im Einsatz, z.B:
* Rosetta (proprietär)
* Archivematica (open source)
* Preservica (proprietär)

Zusätzliche Funktionen können sein: Formatmigration, Integritätsprüfungen, Erhaltungsplanung

auch: Anbindung an Speicherung auf Magnetband (Bps. [bwDataArchiv ](https://www.rda.kit.edu/speichern.php)) möglich

* Modell: https://en.wikipedia.org/wiki/Open_Archival_Information_System


* Archivformate: https://kost-ceco.ch/cms/kad_main_de.html

Der Katalog beschreibt wichtige und verbreitete Dateiformate und analysiert ihre Eignung für die digitale Archivierung.
* Zertifizierung: https://www.coretrustseal.org/
* Konferenz der community: https://www.ipres2026.nz/ oder https://www.langzeitarchivierung.de/Webs/nestor/DE/Veranstaltungen_und_Termine/praxistag/2026praxistag.html



* Beispiel für digital preservation from scratch: https://zenodo.org/records/18829444

*  [Kapitel 1 Einführung / nestor Handbuch: Eine kleine Enzyklopädie der digitalen Langzeitarchivierung](https://nestor.sub.uni-goettingen.de/handbuch/nestor-handbuch_23.pdf)


### Schwammigster Punkt