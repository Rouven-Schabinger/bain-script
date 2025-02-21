---
title: BAIN FS25 - Bibliothekssysteme / Archivsysteme

---

# BAIN FS25 - Bibliothekssysteme / Archivsysteme



## Wiederholung
* Metadatenstandards in Bibliotheken (MARC21)
* Vergleich mir Dublin Core
* Regelwerk, Standard, Datenformat
* Swiss Library Service Platfrom (SLSP)
* Alma
    * Third Party Integration
    * Administration (z.B. Metadatenstandard)
    * Alma im Konsortiummodell (NZ, IZs)
    * Import von Bibliomedia records


## Bibliotheksysteme
### Exkurs Migration 
* Ausgangsdaten: Gleiche Erfassung (RDA) und Format (MARC21) und trotzdem anders
z.B.: https://github.com/Rouven-Schabinger/bain-alma-import/blob/main/000000080_LLB01000502511.xml
* Vgl. ETL-Prozess (später im Kurs)
* Entpacken
* Filtern
* Anreichern/Ergänzen
    * bibliographisches level (z.B. Klassifikation, Inhaltsberzeichnise)
    * Bestandslevel, Exemplarlevel
* Verarbeitbar machen, Batches
* Konkordanz anlegen 
Dublettenprüfung ist komplex, Trainieren eines KI-Modell, ergänzen mit regelbasierten matching. Niemals 100%.
* Verwandtschaftsverhältnisse können schwierig sein, z.B. Buch in Serie oder Artikel in Zeitschrift (analytische Aufnahmen)
* Nach Typ Importieren (Bücher, Serien, physisch-elektronisch ...)
* Tests und Qualitätsprüfung
* **und das sind nur die bibliographischen Daten!**
* ganz konkrete Skripte oft nur einmalig verwendbar, da stark auf Daten angepasst, aber Prozesschritte sind abstrahierbar

**Beispiel Projektplan**
![image](https://hackmd.io/_uploads/SyTWcbU5ye.png)

 

### Vergleich Alma mit Open-Source-System
[Integrated Library Systems](https://en.wikipedia.org/wiki/Integrated_library_system)

* Webseite: <https://koha-community.org>
* Weltweites Open Source Projekt, gegründet 1999 in Neuseeland, heute  mit Beteiligung von Unternehmen wie ByWater Solutions, Biblibre,  Catalyst IT, PTFS Europe, Theke Solutions
* Status des Projekts: Siehe [Statistik bei Open Hub](https://www.openhub.net/p/koha)

Note:
- Zur Gesundheit von Open-Source-Projekten siehe auch https://felixlohmeier.de/slides/2017-09-28_vufind-anwendertreffen-keynote.html
- Zur Bedeutung von Open-Source-Software auch dieser Comic: https://xkcd.com/2347/
(Vielleicht erinnern Sie sich an log4j oder CrowdStrike)
- Verschiedene Business Modelle: https://en.wikipedia.org/wiki/Business_models_for_open-source_software

#### Koha Dokumentation

* Professionelle Entwicklungsstrukturen, vgl. Dashboard: <https://dashboard.koha-community.org>
* Release Notes zur Version 24.11: <https://koha-community.org/koha-24-11-00-released/>
* Handbuch [englisch](https://koha-community.org/manual/23.11/en/html/)

#### Koha Demo (optional)

* MARC21, Koha 24.11 bereitgestellt von schweizer Unternehmen "Admin Kuhn"
  * Dienstoberfläche: https://koha.adminkuhn.ch:8443
  * OPAC: https://koha.adminkuhn.ch:443
* Login mit Benutzername `demo` / Passwort `demo` möglich
* wird jeweils Morgens um 5 Uhr auf Standardwerte zurückgesetzt
* siehe auch die Erläuterungen unter http://adminkuhn.ch/wiki/Koha-Demoinstallation

Die Grundkonfiguration in der Demo-Installation von Koha ist bereits erledigt. 

Live-Beispiel: https://katalog.bibliothek.kit.edu/
Übersicht: https://wiki.koha-community.org/wiki/KohaUsers/Europe#table_row_23


### Übung: Strategische Spielereien

Gruppe 1: Argumentation gegenüber Träger / Direktion

> Sie müssen Ihrer Direktion / dem Träger ein Systemwechsel zu Alma oder koha vorschlagen, welche Argumente führen Sie jeweils auf?
> Wie rechtfertigen Sie den sehr viel höheren Mitteleinsatz bei proprietären Systemen?
>  Sehen Sie Alternativen?

Gruppe 2: Motivation und Kommunikation der beteiligten Bibliotheken

> Wie würden Sie die Bibliotheken miteinbeziehen?
> Wie würden Sie den Change begleiten?
> Welche Kommunikationskanäle würden Sie nutzen?

Gruppe 3: Technische Alternativen Pro und Contra

> Welche Vor- und Nachteile gibt es bei einem cloudbasierten System?
> Gibt es Alternativen zu Alma?
> Wie beurteilt Sie die Konfigurationsmöglichkeiten?

Gruppe 4: e-only Bibliotheken
> Braucht ein e-only Bibliothek überhaupt ein (klassiches) Bibliothekssystem?
    
 ###  Marktüberblick Bibliothekssysteme
**Statistiken zum Markt USA/UK**

* Marshall Breeding veröffentlicht jährlich im American Libraries Magazine den "Library Systems Report" und erfasst dafür regelmässig Statistiken. Daran lässt sich die internationale Entwicklung der Produkte am ehesten ablesen.
https://americanlibrariesmagazine.org/2024/05/01/2024-library-systems-report/

* Übersicht über vergangene Fusionen und Aufkäufe: https://librarytechnology.org/mergers/
Achten Sie hier besonders auf Clarivate.

**Notes**

* Alma ist auf dem aktuellsten Stand der Technik und bietet vorbildliche Programmierschnittstellen.
* Alma ist cloudbasiert, d.h. zentrale Installation auf Servern von Ex Libris und regelmässige Updates.
* Kritiker befürchten langfristig Nachteile durch die Abhängigkeit vom Hersteller Ex Libris und dessen Marktmacht (Vendor Lock-in).
* weiterer Dienstleister / Bibliotheksystem in der Schweiz: https://www.alcoda.info/homepage/




**Unterschiede zwischen wiss. und öff. Bibliothekssoftware:**

* Traditionell gibt es grosse Unterschiede zwischen wissenschaftlichen und öffentlichen Bibliotheken (darunter Schulbibliotheken)
* Bibliotheksmanagementsoftware für öffentliche Bibliotheken enthält oft Module für Veranstaltungsmanagement oder Content-Management (Webseiten), legt Schwerpunkte auf optischer Darstellung (Buchcover, Themenschwerpunkte) und bindet Plattformen für E-Books und Hörbücher ein.
* Bibliotheksmanagementsoftware für wissenschaftliche Bibliotheken legt Schwerpunkte auf Erschliessung, E-Ressourcen-Management (elektronische Zeitschriften) und komplexe Geschäftsgänge



## Archivsysteme

### Metadatenstandards in Archiven: ISAD(G) und EAD

* [Seeing Standards: A Visualization of the Metadata Universe](https://jennriley.com/metadatamap)

### Regelwerk: ISAD(G)

- Als digitale Archivsysteme entwickelt wurden, orientierte sich die Datenstruktur an analogen Findmitteln wie Findbüchern und Zettelkästen (physische Welt).
- Ein wichtiger Verzeichnungsstandard im Archivwesen wurde 1994 (Revision 2000) eingeführt, die "International Standard Archival Description (General)" - kurz [ISAD(G)](https://de.wikipedia.org/wiki/ISAD(G)).
- Grundsätzlich gibt es hier eine mehrstufige Verzeichnung im Provenienzprinzip, um den Entstehungszusammenhang abzubilden.

#### Informationsbereiche

Der Standard enthält 26 Verzeichnungselemente in 7 Informationsbereichen:

1. Identifikation
2. Kontext
3. Inhalt und innere Ordnung
4. Zugangs- und Benutzungsbedingungen
5. Sachverwandte Unterlagen
6. Anmerkungen
7. Kontrolle

#### Pflichtfelder

Von besonderer Bedeutung sind 6 Pflichtfelder:

- Signatur
- Titel
- Provenienz
- Entstehungszeitraum
- Umfang
- Verzeichnungsstufe


#### Beispiel

![The-ISADG-hierarchical-model-see-online-version-for-colours](https://hackmd.io/_uploads/H1h5qXYDyl.png)

Bsp. Notizblatt < Mappe < Sammlung < Nachlass/Vorlass


#### Grenzen von ISAD(G)

1. Ein einzelner Datensatz ist unter Umständen nur im Kontext verständlich (z. B. nur "Protokoll" als Titel).
2. Die Tektonik ist eindimensional (keine Mehrfachzuordnung möglich).
3. Der Standard enthält keine Vorgaben zur Digitalisierung oder zur digitalen Langzeitarchivierung.

#### Normdaten mit ISAD(G)

- Um Normdateien verzeichnen zu können, wurde später ein ergänzender Standard "International Standard Archival Authority Record for Corporate Bodies, Persons, and Families" - kurz [ISAAR(CPF)](https://de.wikipedia.org/wiki/ISAAR(CPF)) verabschiedet. Dieser wird in der Praxis wegen dem Zusatzaufwand bei der Erschliessung jedoch nur selten verwendet.
- Aktuell ist ein neuer Standard ["Records in Contexts" (RIC)](https://de.wikipedia.org/wiki/Records_in_Contexts) in Entwicklung. Dieser basiert auf Linked-Data-Prinzipien und soll neue und mehrfache Beziehungen zwischen Entitäten ermöglichen.

Note:

- In den Archiven der ETH-Bibliothek ist wegen der Bibliothekszugehörigkeit die [GND](https://de.wikipedia.org/wiki/Gemeinsame_Normdatei)-ID von besonderer Bedeutung.
- Projektgruppe [ENSEMEN](https://vsa-aas.ch/verein/arbeitsgruppen/ensemen/) arbeitete an einer schweizerischen Ausprägung des neuen Standards [Records in Contexts](https://www.ica.org/en/records-contexts-german) (RiC), mit Beteiligung der FH Graubünden

### Übung: Archivkataloge

- Suchen Sie nach:
  - `Einstein` im [Online Archivkatalog des Staatsarchivs BS](https://query.staatsarchiv.bs.ch/query/suchinfo.aspx)
  - `Einstein Ehrat` im [Hochschularchiv ETH Zürich](http://archivdatenbank-online.ethz.ch/)
- Beantworten Sie die folgenden Fragen:
  1. Welche Informationen enthält die Trefferliste?
  2. Welche Verzeichnungsstufen sind vertreten?
  3. Sind die ISAD(G)-Informationsbereiche erkennbar?
  4. Decken sich die grundlegenden Informationen oder gibt es bemerkenswerte Unterschiede?
  5. Worin liegen die zentralen Unterschiede zu einem Bibliothekskatalog?
- Zum Nachschlagen: [ISAD(G) Guidelines](https://www.ica.org/app/uploads/2024/01/CBPS_2000_Guidelines_ISADG_Second-edition_DE.pdf)

### Fragen / Erkenntnisse


### Datenformat: EAD

- [Encoded Archival Description](https://de.wikipedia.org/wiki/Encoded_Archival_Description) (EAD) ist ein XML-Standard
- Verschiedene Versionen: EAD2002 und EAD3 (seit 2015; aktuell ist 1.1.1 von 2019)
- Lässt viele Wahlmöglichkeiten offen, daher gibt es oft Anwendungsprofile, die genauer spezifizieren welche Werte zugelassen sind.
- Anwendungsfälle: [Archives Portal Europa](https://www.archivesportaleurope.net/), [Archivportal-D](https://www.archivportal-d.de), [Kalliope](https://kalliope-verbund.info)
- Einführung: [Nicolas Moretto (2014): EAD und digitalisiertes Archivgut](https://wiki.dnb.de/download/attachments/90410326/20140414_KIMWS_EAD.pdf?version=1&modificationDate=1398246420000&api=v2). Präsentation auf dem [DINI AG KIM Workshop 2014](https://wiki.dnb.de/display/DINIAGKIM/KIM+WS+2014) in Mannheim.

Note:

- Wir werden später praktisch mit EAD-Dateien arbeiten, daher hier nur diese Kurzinfo.
- Die Präsentationsfolien von Nicolas Moretto geben einen guten Überblick über EAD2002.
- Liste der Elemente [in EAD2002](https://eadiva.com/2/elements/) und [in EAD3](https://eadiva.com/elements/)

### Aktuelle Entwicklungen

- Umstieg von ISAD(G) auf RiC wird mit viel Aufwand verbunden sein, auch mit einem Systemwechsel. Bsp. https://icae.esrc.info/
- Generierung von mehr Volltexten u.a. durch Optical Character Recognition (OCR) auch für Handschriften. Automatisierte Anreicherung von Volltexten durch Named Entity Recognition.
- In Wikidata werden Online-Findmittel über Property [Archives at](https://www.wikidata.org/wiki/Property:P485) verzeichnet. Beispiel [Albert Einstein in Wikidata](https://www.wikidata.org/wiki/Q937).
- In der Schweiz gibt es eine Vernetzungsinitiative [Metagrid](https://metagrid.ch) und weitere Dienste von [histHub](https://histhub.ch), einer Forschungsplattform für die Historischen Wissenschaften.
- Metasuche Swisscollections: https://swisscollections.ch
- Literaturempfehlung: [Umfrage "Was sich Historiker*innen von Archiven wünschen"](https://dhdhi.hypotheses.org/6107)
- Archivportale der Schweiz: https://www.infoclio.ch/de/archive
    
    