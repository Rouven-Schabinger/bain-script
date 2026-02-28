# BAIN FS26 - Bibliothekssysteme / Archivsysteme



## Wiederholung
* Bibliotheksysteme: QUIZ
* Metadatenstandards in Bibliotheken (MARC21)
* Vergleich mir Dublin Core
    * Ja, MARC bildet Beziehungen in der Regel strukturierter und differenzierter ab als einfaches Dublin Core (z.B. dc:relation), Qualified Dublin Core kann mehr (z.B. Einbeziehung anderer Eigenschaften wie dcterms:hasVersion)
* Regelwerk, Standard, Datenformat
* Swiss Library Service Platform (SLSP)
* Alma
    * Third Party Integration
    * Administration (z.B. Metadatenstandard)
    * Alma im Konsortiummodell (NZ, IZs)
    * Import von Bibliomedia records (Bedeutung von Lokalfeldern und [Normalisierungregel](https://developers.exlibrisgroup.com/blog/alma-normalization-rule-examples/))


## Bibliotheksysteme
### Exkurs Migration 
* Aus technischer Sicht spielen Migrationen in Bibliotheken eine zentrale Rolle, um Daten, Metadaten und Fachanwendungen langfristig interoperabel, sicher und nutzbar zu halten – insbesondere beim Wechsel von Systemen, Formaten oder Infrastrukturplattformen.

* Ausgangsdaten: Gleiche Erfassung (RDA) und Format (MARC21) und trotzdem anders
z.B. Daten aus der Uni Liechtenstein: https://github.com/Rouven-Schabinger/bain-alma-import/blob/main/000000080_LLB01000502511.xml
* Vgl. **ETL-Prozess** (später im Kurs)
* Entpacken
* Filtern
* Anreichern/Ergänzen
    * bibliographisches level (z.B. Klassifikation, Inhaltsverzeichnisse)
    * Bestandslevel, Exemplarlevel
* Verarbeitbar machen in Paketen (Batches). Warum ist das sinnvoll?
* Konkordanz anlegen 
Dublettenprüfung ist komplex, Trainieren eines KI-Modell, ergänzen mit regelbasierten matching. Niemals 100%.
    * Matches können auch angereichert werden (z.B. Sacherschliessung)
    * Problemfälle: z.B. Mehrbändige Werke
    * Ausschluss von Altbestand
* Verwandtschaftsverhältnisse können schwierig sein, z.B. Buch in Serie oder Artikel in Zeitschrift (analytische Aufnahmen)
* Nach Typ Importieren (Bücher, Serien, physisch-elektronisch ...)
* Tests und Qualitätsprüfung
* **und das sind nur die bibliographischen Daten!**
* ganz konkrete Skripte oft nur einmalig verwendbar, da stark auf Daten angepasst, aber Prozesschritte sind abstrahierbar

**Beispiel Projektplan**
![image](https://hackmd.io/_uploads/SyTWcbU5ye.png)

* Migrationen bei SLSP: [Konferenzbeitrag](https://igelu.org/wp-content/uploads/2025/10/Room103_Tuesday_DIY_HowToIntegrateNewLibraries.pdf)

zum Denken:

* Warum sind „Datenbereinigungen“ keine kosmetische, sondern eine funktionale Voraussetzung für Migrationen?


* Warum reichen Standard-Migrations-Tools (hier: Ex Libris) bei komplexen Verbundstrukturen / Konsortien oft nicht aus?

### Vergleich Alma mit Open-Source-System
[Integrated Library Systems](https://en.wikipedia.org/wiki/Integrated_library_system)

* Webseite: <https://koha-community.org>
* Weltweites Open Source Projekt, gegründet 1999 in Neuseeland, heute  mit Beteiligung von Unternehmen wie ByWater Solutions, Biblibre,  Catalyst IT, PTFS Europe, Theke Solutions
* Status des Projekts: Siehe [Statistik bei Open Hub](https://www.openhub.net/p/koha)
* Professionelle Entwicklungsstrukturen, vgl. Dashboard: <https://dashboard.koha-community.org>
* Release Notes : <https://koha-community.org/koha-24-05-12-released/>
* Handbuch (https://koha-community.org/manual/latest/de/html/index.html). Hier ist besonders der Installationsteil zu berücksichtigen.
* Wie würde man koha ausprobieren wenn man nicht selbst installieren will? Vgl. Sandbox
    * https://koha-community.org/demo/
    * wird jeweils Morgens um 5 Uhr auf Standardwerte zurückgesetzt
    * siehe auch die Erläuterungen unter http://adminkuhn.ch/wiki/Koha-Demoinstallation

Die Grundkonfiguration in der Demo-Installation von Koha ist bereits erledigt. 

* Live-Beispiel: https://katalog.bibliothek.kit.edu/
* Übersicht: https://wiki.koha-community.org/wiki/KohaUsers/Europe


Note:
- Zur Gesundheit von Open-Source-Projekten siehe auch https://felixlohmeier.de/slides/2017-09-28_vufind-anwendertreffen-keynote.html
- Zur Bedeutung von Open-Source-Software auch dieser Comic: https://xkcd.com/2347/
(Vielleicht erinnern Sie sich an log4j oder CrowdStrike)
- Verschiedene Geschäftsmodelle auch für Open Soure: https://de.wikipedia.org/wiki/Gesch%C3%A4ftsmodelle_f%C3%BCr_Open-Source-Software
- Netzwerk SDS - Souveräne Digitale Schweiz, auch zu Cloudsystemen generell letzte Folie: https://nextcloud.bfh.science/index.php/s/wF8Px3HNE5dXCsK?dir=/&openfile=true 



### Übung: Strategische Spielereien

Frage 1: Argumentation gegenüber Träger / Direktion

> Sie müssen Ihrer Direktion / dem Träger ein Systemwechsel zu Alma oder koha vorschlagen, welche Argumente führen Sie jeweils auf?
> Wie rechtfertigen Sie den sehr viel höheren Mitteleinsatz bei proprietären Systemen?
>  Sehen Sie Alternativen?


Frage 2: Technische Alternativen Pro und Contra

> Welche Vor- und Nachteile gibt es bei einem cloudbasierten System?
> Wie beurteilt Sie die Konfigurationsmöglichkeiten?

Frage 3: e-only Bibliotheken
> Braucht ein e-only Bibliothek überhaupt ein (klassisches) Bibliothekssystem?
> Wie würden Sie das Change Management Weg von einem Biblitothekssystem gestalten?


Zum Denken:
> Maybe most expensive sentence: lets build it on or own

 ###  Marktüberblick Bibliothekssysteme
**Statistiken zum Markt USA/UK**

* Marshall Breeding veröffentlicht jährlich im American Libraries Magazine den "Library Systems Report" und erfasst dafür regelmässig Statistiken. Daran lässt sich die internationale Entwicklung der Produkte am ehesten ablesen.
https://americanlibrariesmagazine.org/2025/05/01/2025-library-systems-report/

* Übersicht über vergangene Fusionen und Aufkäufe: https://librarytechnology.org/mergers/
Achten Sie hier besonders auf Clarivate. Wir kommmen bei den Discovery-Systemen nochmal darauf zurück.

**Notes**

* Alma ist auf dem aktuellsten Stand der Technik und bietet vorbildliche Programmierschnittstellen.
* Alma ist cloudbasiert, d.h. zentrale Installation auf Servern von Ex Libris und regelmässige Updates.
* Kritiker befürchten langfristig Nachteile durch die Abhängigkeit vom Hersteller Ex Libris und dessen Marktmacht (Vendor Lock-in).
* weitere Dienstleister / Bibliotheksysteme in der Schweiz: 
    * https://www.alcoda.info/homepage/
    * https://www.rero.ch/en/produits/ils
    * https://www.predata.ch/Bibliothekssoftware-1/winMedio 
    * https://www.axiell.com/solutions/product/quria/




**Unterschiede zwischen wiss. und öff. Bibliothekssoftware:**

* Traditionell gibt es grosse Unterschiede zwischen wissenschaftlichen und öffentlichen Bibliotheken (darunter Schulbibliotheken)
* Bibliotheksmanagementsoftware für öffentliche Bibliotheken enthält oft Module für Veranstaltungsmanagement oder Content-Management (Webseiten), legt Schwerpunkte auf optischer Darstellung (Buchcover, Themenschwerpunkte) und bindet Plattformen für E-Books und Hörbücher ein.
* Bibliotheksmanagementsoftware für wissenschaftliche Bibliotheken legt Schwerpunkte auf Erschliessung, E-Ressourcen-Management (elektronische Zeitschriften) und komplexe Geschäftsgänge







## Archivsysteme

### Metadatenstandards in Archiven: ISAD(G) und EAD

* [Seeing Standards: A Visualization of the Metadata Universe](https://jennriley.com/wp-content/uploads/2025/07/seeingstandards.pdf)

### Regelwerk: ISAD(G)

- Als digitale Archivsysteme entwickelt wurden, orientierte sich die Datenstruktur an analogen Findmitteln wie Findbüchern und Zettelkästen (physische Welt).
- Ein wichtiger Verzeichnungsstandard im Archivwesen wurde 1994 (Revision 2000) eingeführt, die "International Standard Archival Description (General)" - kurz [ISAD(G)](https://de.wikipedia.org/wiki/ISAD(G)).
- Grundsätzlich gibt es hier eine mehrstufige Verzeichnung im Provenienzprinzip, um den Entstehungszusammenhang abzubilden.
- Auch MARC hat etwas zur Provenienz: https://www.loc.gov/marc/bibliographic/bd561.html - Angabe im Online-Katalog nicht immer gewünscht bei Schenkern aber interessant für z.B. Geschichtswissenschaft. Welche Ebene ist sinnvoll (bibliographisch oder Bestand)?

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
*ISAD(G)*

![image](https://hackmd.io/_uploads/BJJWZhxKZl.png)
* nach den schweizerischen Richtlinien für die Umsetzung von
ISAD(G)*

Bsp. Notizblatt < Mappe < Sammlung < Nachlass/Vorlass


#### Grenzen von ISAD(G)

1. Ein einzelner Datensatz ist unter Umständen nur im Kontext verständlich (z. B. nur "Protokoll" als Titel).
2. Die Tektonik ist eindimensional (keine Mehrfachzuordnung möglich).
3. Der Standard enthält keine Vorgaben zur Digitalisierung oder zur digitalen Langzeitarchivierung.

#### Normdaten mit ISAD(G)

- Um Normdateien verzeichnen zu können, wurde später ein ergänzender Standard "International Standard Archival Authority Record for Corporate Bodies, Persons, and Families" - kurz [ISAAR(CPF)](https://de.wikipedia.org/wiki/ISAAR(CPF)) verabschiedet. Dieser wird in der Praxis wegen dem Zusatzaufwand bei der Erschliessung jedoch nur selten verwendet.


Note:

- In den Archiven der ETH-Bibliothek ist wegen der Bibliothekszugehörigkeit die [GND](https://de.wikipedia.org/wiki/Gemeinsame_Normdatei)-ID von besonderer Bedeutung.


### Übung: Archivkataloge

- Suchen Sie nach:
  - `Einstein` im [Online Archivkatalog des Staatsarchivs BS](https://query.staatsarchiv.bs.ch/query/suchinfo.aspx)
  - `Einstein Ehrat` im [Hochschularchiv ETH Zürich](https://vls.hsa.ethz.ch/client/)


- Beantworten Sie die folgenden Fragen:
  1. Welche Informationen enthält die Trefferliste?

 
  2. Welche Verzeichnungsstufen sind vertreten?

 
  3. Sind die ISAD(G)-Informationsbereiche erkennbar?


  4. Decken sich die grundlegenden Informationen oder gibt es bemerkenswerte Unterschiede?


  5. Worin liegen die zentralen Unterschiede zu einem Bibliothekskatalog?

 


- Zum Nachschlagen: [ISAD(G) Guidelines](https://www.ica.org/app/uploads/2024/01/CBPS_2000_Guidelines_ISADG_Second-edition_DE.pdf)


### Datenformat: EAD

- [Encoded Archival Description](https://en.wikipedia.org/wiki/Encoded_Archival_Description) (EAD) ist ein XML-Standard
- Verschiedene Versionen: EAD2002 und [EAD3](https://www.loc.gov/ead/) (seit 2015; aktuell ist 1.1.1 von 2019): 
- Lässt viele Wahlmöglichkeiten offen, daher gibt es oft Anwendungsprofile, die genauer spezifizieren welche Werte zugelassen sind.
- Anwendungsfälle: [Archives Portal Europa](https://www.archivesportaleurope.net/), [Archivportal-D](https://www.archivportal-d.de), [Kalliope](https://kalliope-verbund.info)
- Einführung: [Nicolas Moretto (2014): EAD und digitalisiertes Archivgut](https://wiki.dnb.de/download/attachments/90410326/20140414_KIMWS_EAD.pdf?version=1&modificationDate=1398246420000&api=v2). Präsentation auf dem [DINI AG KIM Workshop 2014](https://wiki.dnb.de/display/DINIAGKIM/KIM+WS+2014) in Mannheim. Schon etwas älter, aber Standard stabil .
- [RiC und EAD / ISAD(G) im Wechselspiel
Kompatibilität und Konvertierbarkeit](https://www.bundesarchiv.de/assets/bundesarchiv/de/Downloads/KLA/KLA_20240423_AFIS_RIC-WORKSHOP_ARNOLD.pdf)

Note:

- Wir werden später praktisch mit EAD-Dateien arbeiten, daher hier nur diese Kurzinfo.
- Die Präsentationsfolien von Nicolas Moretto geben einen guten Überblick über EAD2002.
- Liste der Elemente [in EAD2002](https://eadiva.com/2/elements/) und [in EAD3](https://eadiva.com/elements/)



### RiC (Records in Context)

- Aktuell ist ein neuer Standard ["Records in Contexts" (RIC)](https://de.wikipedia.org/wiki/Records_in_Contexts) in Entwicklung. Dieser basiert auf Linked-Data-Prinzipien und soll neue und mehrfache Beziehungen zwischen Entitäten ermöglichen.

- [Einführungsfolien](https://www.bundesarchiv.de/assets/bundesarchiv/de/Downloads/KLA/KLA_20240423_AFIS_RIC-WORKSHOP_JAGODZINSKI.pdf): 
    - Erwähnter Converter: https://archivesnationalesfr.github.io/rico-converter/en/

* [Anwendungsrichtlinien](https://ica-egad.github.io/RiC-AG/table_of_contents.html)

- Und was ist das Format? Mögliche Serialisierungsformate

Da RiC auf RDF basiert, kann man es in allen RDF-Formaten serialisieren:

| Format                | Typisch für                         |
|-----------------------|-------------------------------------|
| RDF/XML               | ältere Semantic-Web-Umgebungen      |
| Turtle (.ttl)         | sehr verbreitet, gut lesbar         |
| JSON-LD               | Web-Anwendungen                     |
| N-Triples   | Datenaustausch / Triplestores       |



- Projektgruppe [ENSEMEN](https://vsa-aas.ch/verein/arbeitsgruppen/ensemen/) arbeitete an einer schweizerischen Ausprägung von RiC, mit Beteiligung der FH Graubünden. Jetzt AG: https://vsa-aas.ch/verein/arbeitsgruppen/normen-und-standards/

- Beispiel: https://icae.esrc.info/


**Sonstiges**
- **eCH-0160** ist der Schweizer eGovernment-Standard, der den Austausch archivischer Erschliessungsdaten regelt,
während **XISADG** das darin definierte konkrete XML-Schema ist, das ISAD(G)-Elemente technisch strukturiert abbildet.

**Ausblick:**
- Generierung von mehr Volltexten relevant für u.a. durch Optical Character Recognition (OCR) auch für Handschriften. Automatisierte Anreicherung von Volltexten durch Named Entity Recognition.
- In Wikidata werden Online-Findmittel über Property [Archives at](https://www.wikidata.org/wiki/Property:P485) verzeichnet. Beispiel [Albert Einstein in Wikidata](https://www.wikidata.org/wiki/Q937).
- In der Schweiz gibt es eine Vernetzungsinitiative [Metagrid](https://metagrid.ch/search/?query=albert+einstein) und weitere Dienste von [histHub](https://histhub.ch), einer Forschungsplattform für die Historischen Wissenschaften (Verlinkungstool).
- Metasuche Swisscollections: https://swisscollections.ch
- Archivportale der Schweiz: https://www.infoclio.ch/de/archive

### Übung (und Vorbereitung nächste Woche)

- [Archival Linked (Open) Data](https://doi.org/10.18755/iw.2020.17)
- Lesen Sie Kapitel: "Linked Open Data in Archiven" S. 336 bis ausschliesslichlich "Von ISAD(G) und ISAAR(CPF) zu Open Data" S. 341
1.  Welche Gründe führen laut Text dazu, dass sich Archive zunehmend mit Linked Open Data beschäftigen, und welche Vorteile versprechen sie sich davon?
2. Welche Bedeutung haben Normdaten (GND, VIAF) und nationale Initiativen (z. B. ENSEMEN) für die Umsetzung von Linked Open Data in Archiven?
3. In welchen Bereichen können Archive von den Erfahrungen der Bibliotheken mit Linked Open Data profitieren, und wo bestehen strukturelle Unterschiede?

# Literatur 

Migration:
- Kapitel 11 und 12 von:  Von NEBIS zu SLSP
Wie die Datenmigration des grössten Schweizer Verbundes umgesetzt wurde  https://doi.org/10.5282/o-bib/5738 

KI im Archiv:
- [Mit Künstlicher Intelligenz zu besserer Nutzbarkeit](https://www.degruyter.com/document/doi/10.1515/abitech-2025-0003/html)


