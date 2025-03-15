# BAIN FS25 - Repository-Software für Publikationen und Forschungsdaten

- Agenda & Recap




## Open Access und Open Data

* Was ist ein Repositorium? Welche kennt ihr?

- **Publikationen**
  - Open Access, vgl. https://consortium.ch/
  - [Statistik zu Open-Access-Repositorien](https://web.archive.org/web/20240328063306/https://v2.sherpa.ac.uk/view/repository_visualisations/1.html )
  - Fokus: Zweitveröffentlichungen ("grüner Weg") und Hochschulschriften
  
- **Forschungsdaten**
  - Open Data
  - Transparenz und Repoduzierbarkeit [Open Science](https://en.wikipedia.org/wiki/Open_science)
  - [Verzeichnis von Forschungsdaten-Repositorien](https://www.re3data.org)
      - Länder, Typen, Communities, Langzeitarchivierung, PID, Forschungssoftware
      - Schema: https://www.re3data.org/schema
      - restful API/Jupyter Notebook: https://coref.project.re3data.org/blog/using_the_re3data_api
  - Fokus: Primärdaten, die bei der Forschung entstehen. Oft Daten als Anhang zu Zeitschriftenartikeln, aber auch auch als eigenständige Publikation möglich


  --> wichtiges Arbeitsfeld für Infrastrukturanbieter in der Hochschullandschaft (z.B. Bibliotheken)


- Bsp. Verknüpfung Forschungsdatum und Publikation:

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
    - der query soll ihrere Suche in der GUI entsprechen
    - extrahieren Sie zusätzlich noch den "Umfang" des Repositoriums


#### Erkenntnisse / Fragen ####
*

### Forschungsinformationen

- Informationen über Forschende, Drittmittelprojekte, Patente und vieles mehr.
- Ziel ist die Forschungsberichterstattung. Um die Daten zusammenzuführen und Berichte erstellen zu können, werden oft Forschungsinformationssysteme an den Universitäten eingeführt.
- Beispiel: ["Kerndatensatz Forschung" in Deutschland](https://kerndatensatz-forschung.de/version1/technisches_datenmodell/v_1_3/ER-Modell.html)
- Zum Stand in der Schweiz: Ackermann Krzemnicki, Sonia and Hägele, Bernd F. (2016): Die Standardisierung von Forschungsinformationen an Schweizer universitären Hochschulen. https://edoc.unibas.ch/54788/



 **Government Data** oder **OER** (Open Educational Resources)
    - https://opendata.swiss/de
    - https://oer-repository.switch.ch/edu-sharing/components/search?q=


Konvergenz:
  - als Plattform: https://opendatanavigator.switch.ch/
  - Als Modell: https://datacite.org/blog/introducing-the-pid-graph/ DataCite


### Beispiele

- [Zenodo](https://zenodo.org) (InvenioRDM), vgl. https://github.com/zenodo/zenodo
    - Upgrade-Probleme: https://blog.zenodo.org/2023/10/19/2023-10-19-upgrade-issues/
- [PHSG Proforis](https://proforis.phsg.ch/home) (DSpace-CRIS)


## Übungen mit DSpace

Standardfragen IT:

- Make or Buy
- Authentifizierung (z.b Edu-ID, ORCID), Rollen und Rechte
    - vgl. https://help.switch.ch/aai/

### Einführung in DSpace

- Software geeignet für Publikationen und Forschungsdaten
- Erweiterung für Forschungsinformationen: DSpace-CRIS
- Metadatenstandard: Qualified Dublin Core, kann aber auch mit [DataCite](https://schema.datacite.org/) Metadatenschema betrieben werden.
- DSpace 6: 2016 erstmalig veröffentlicht , wird nicht mehr weiterentwickelt und der [Support endete am 1.7.2023](https://wiki.lyrasis.org/display/DSPACE/Support+for+DSpace+5+and+6+is+ending+in+2023)
- DSpace 7: im August 2021 veröffentlicht , neue Technologien im Frontend (Angular) und Backend (neue REST API)
- DSpace 8: Juni 2024: generelle Verbesserungen

### DSpace Demo

Aus Zeitgründen keine Installation, nur Test mit öffentlich zugänglicher Demo.

DSpace Demo: https://demo.dspace.org

Wird laufend aktualisiert

- Site Administrator: `dspacedemo+admin@gmail.com`
- Community Administrator: `dspacedemo+commadmin@gmail.com`
- Collection Administrator: `dspacedemo+colladmin@gmail.com`
- Submitter: `dspacedemo+submit@gmail.com`
- Passwort immer: `dspace`

### Übung: Communities und Collections

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


### Einreichung und Review

DSpace Demo: https://demo.dspace.org

* Um Rechteprobleme zu vermeiden, Login mit DSpace-Admin
* MyDspace bei Login-Button aufrufen
* Neues Dokument anlegen (z.B. "Veröffentlichung"), Daten aus Datenbank übernehmen, Datei hochladen. Sammlung: 1-step-workflow
* In MyDSpace auf "Zeige Aufgaben" wechseln. Dort werden Dokumente zur Bearbeitung/Freigabe aufgeführt

### Import und Export

- DSpace bietet auch dateibasierten Import, besonders relevant sind im Kontext von Repositorien aber die Schnittstellen:
  - SWORD ermöglicht die Publikation in DSpace (Metadaten und Datei-Upload) von einer anderen Webseite aus (z.B. Intranet der Hochschule).
  - OAI-PMH ermöglicht es externen Systemen die in DSpace verzeichneten Metadaten abzurufen.
- OAI-PMH-Schnittstelle der DSpace-Demo (Daten erscheinen dort zeitverzögert): http://demo.dspace.org/oai/request?verb=ListSets
- Beispiel für Portal auf Basis von OAI-PMH: Die [Bielefeld Academic Search Engine (BASE)](https://www.base-search.net/) "erntet" weltweit OAI-PMH-Schnittstellen und verzeichnet damit weit über 250 Mio. Dokumente.

Note:

* [SWORD](https://en.wikipedia.org/wiki/SWORD_(protocol)) ist eine Schnittstelle, um Publikationen in einem Repository abzuliefern. Damit kann ein Formular mit Dateiupload auf einer Webseite (außerhalb der Repository-Webseite) angeboten werden.
* Um Daten aus dem Repository auf Webseiten anzuzeigen, z.B. eine Publikationsliste, werden andere Schnittstellen wie [RSS-Feeds](https://de.wikipedia.org/wiki/RSS_(Web-Feed)) verwendet.

### Übung Beispielpublikation
- Suchen Sie sich bitte schon einmal eine Beispielpublikation aus, die Sie in unsere gemeinsame Testcollection einreichen können.

### Literatur zu DSpace

- Präsentationsfolien und Videomitschnitte der Präsentationen auf den jährlichen D/A/CH-Anwendertreffen:
  - 2024: https://wiki.lyrasis.org/display/DSPACE/DSpace+Praxistreffen+2024 (Diese Woche 2025)
- Q&A zu DSpace-CRIS Entwicklung: https://docs.google.com/document/d/17HSFV6qY48yInfL4zQj1hRsWG-9dHFyGmEksNakVZ7Y/edit
- Suchmaschinenoptimierung (SEO): [Abschnitt im Nutzerhandbuch von DSpace zu SEO](https://wiki.lyrasis.org/display/DSDOC8x/Search+Engine+Optimization)



## Marktüberblick Repository-Software

- Grundsätzliches zu Repositorien: https://open-access.network/informieren/publizieren/repositorien
- Open Directory of Open Access Repositories (OpenDOAR): https://v2.sherpa.ac.uk/opendoar/
a.ac.uk/view/repository_by_country/Switzerland.default.html)

- Instanzen in der Schweiz: https://forschungsdaten.info/fdm-im-deutschsprachigen-raum/schweiz/rdm-infrastructure-repositories/repositories/

### Relevante Systeme in D/A/CH


- [DSpace](https://www.dspace.org)
- [EPrints](https://www.eprints.org)
- [Fedora](http://fedorarepository.org) / [Islandora](https://islandora.ca)
- [InvenioRDM](https://invenio-software.org/products/rdm/)
  - besonders interessant, weil seit Oktober 2023 die Basis von Zenodo am CERN
- [MyCoRe](https://www.mycore.de)
- [OPUS](https://www.opus-repository.org)
- Alma digital: https://knowledge.exlibrisgroup.com/Alma/Training/Alma_Digital/01_Alma_Digital%3A_Overview und bald: https://www.meetspecto.com/
    - z.B. https://www.alexandria.ch/discovery/collectionDiscovery?vid=41BIG_INST:ALEX&lang=de

![image](https://hackmd.io/_uploads/S1n0FRfnJl.png)

- FHGR?
- Wechsel: https://journal.code4lib.org/articles/17398
  - gerade war Code4Lib Conference: https://2025.code4lib.org/


FYI:
-  Zweitveröffentlichungsrecht in der Schweiz: https://www.uzh.ch/blog/ub/2023/05/31/das-projekt-zweitveroeffentlichungsrecht-und-open-access-als-regulatorische-herausforderung-hintergrund-und-projektziele/
