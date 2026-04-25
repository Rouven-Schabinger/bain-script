# BAIN FS26 - Metadaten modellieren und Schnittstellen nutzen

## Rückblick Openrefine
* Quiz

## Ausgangsdaten

* hier kommt alles aus den vorheringen Sessions zusammen


![DOAJ Article Processing-2026-04-25-084614](https://hackmd.io/_uploads/rk0YyW5aWg.png)

made with: https://mermaid.live/


* Alma: MARCXML via SRU aus HPH Sandbox
* Context: EAD via Export aus Sandbox
* DSpace: DC via OAI-PMH aus Demo-Installation
* OpenRefine: MARCXML aus CSV generiert mit Templating Exporter

## Schnittstellen

### Austauschprotokolle für Metadaten (OAI-PMH, SRU)

Es gibt zahlreiche Übertragungsprotokolle im Bibliotheks- und Archivbereich. Drei davon sind besonders weit verbreitet:

* [Z39.50](https://www.loc.gov/z3950/agency/) (Library of Congress)
* [SRU](https://www.loc.gov/sru) - Search/Retrieve via URL (Library of Congress)
* [OAI-PMH](https://www.openarchives.org/pmh/) - Open Archives Initiative Protocol for Metadata Harvesting (Open Archives Initiative)

Welches Protokoll für welchen Zweck?
* Während Z39.50 und SRU sich besonders für Live-Abfragen oder gezielten Datenabruf mit vielen Parametern eignet, zielt OAI-PMH vor allem auf größere Datenabzüge und regelmäßige Aktualisierungen.
* Z39.50 ist sehr alt, aber immer noch im Einsatz (oft aus   Kompatibilitätsgründen), z.B. auch bei Literaturverwaltungsprogrammen. Meist wird das modernere SRU als Ergänzung angeboten. Das Schöne an SRU und OAI-PMH ist, dass die Anfragen als Internetadresse (URL) zusammengestellt werden können und direkt über den Browser ohne Zusatzsoftware aufrufbar sind.
* Vgl. https://en.wikipedia.org/wiki/Contextual_Query_Language

### Konfiguration am Beispiel Alma 
* Wir gehen wieder in die HPH Sandbox
* Dokumentation für  Schnittstellen, Bsp. OAI: https://developers.exlibrisgroup.com/alma/integrations/oai/
* logisches Set machen mit records
* [Publishing Profile](https://knowledge.exlibrisgroup.com/Alma/Product_Documentation/010Alma_Online_Help_(English)/040Resource_Management/075Publishing_Profiles/020Publishing_and_Inventory_Enrichment_(General_Publishing))

* [Integration Profile](https://knowledge.exlibrisgroup.com/Alma/Product_Documentation/010Alma_Online_Help_(English)/090Integrations_with_External_Systems/030Resource_Management/060Setting_Up_OAI_Integration)

* [deleted records](https://www.openarchives.org/OAI/openarchivesprotocol.html#DeletedRecords)
```
<record xmlns="http://www.openarchives.org/OAI/2.0/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <header status="deleted">
    <identifier>oai:alma.41SLSP_NETWORK:991171842270505501</identifier>
    <datestamp>2024-03-12T13:55:32Z</datestamp>
    <setSpec>ext_db2</setSpec>
  </header>
</record>
```


### Metadaten über OAI-PMH und SRU harvesten

* Codespace aufrufen mit vorbereitetem Repository (als Juypterlab)
https://github.com/Rouven-Schabinger/bain-jupyter-codespaces

WORKAROUND: in Browser URL und dann via https://jupyter.org/try-jupyter/lab/ notebook hochladen

* [OAI Requests Spezifikation](https://www.openarchives.org/OAI/openarchivesprotocol.html#ProtocolMessages)
* [Sickle](https://sickle.readthedocs.io/en/latest/)
* [Alma SRU Wrapper](https://almasru.readthedocs.io/en/latest/index.html#) für [Alma SRU](https://developers.exlibrisgroup.com/alma/integrations/sru/)
    * Was ist ein Wrapper?

**Aufgabe**: 
* Alma SRU: Parameter ergänzen für Schlagwortsuche nach "Graubünden"
    * Das wäre Suche über alles nach "history": alma.all_for_ui=history
    * Alle Parameter https://eu03-psb.alma.exlibrisgroup.com/view/sru/41SLSP_HPH?version=1.2&operation=explain
* DSpace OAI: Kürzel für Metadatenformat ermitteln 
    * Hier anfangen: https://demo.dspace.org/server/oai/request?verb=Identify
    * Wie würde man auf ein Set einschränken?
* Harversting ausführen in diesem Notebook: *harvesting.ipynb*
* Code nachvollziehen, Fragen notieren
* Download von Beispiel-records und überprüfen der XML-Struktur





## Konvertierung


### XSLT Crosswalks

* Wir haben Daten in verschiedenen Formaten (MARC21-XML, EAD und DC) vorliegen.
* Nun werden wir diese einheitlich in MARC21-XML konvertieren.
* Crosswalks
  * Gängiger Begriff, um die Konvertierung von einem Metadatenstandard in einen anderen zu beschreiben.
  * Beispiel: Dublin Core zu MARC21.
  * Der "Crosswalk" beinhaltet Regeln wie Elemente und Werte zugeordnet werden (sog. Mapping). Bsp. https://doi.org/10.5281/zenodo.5176122, https://doi.org/10.5281/zenodo.6948238
  * Im Idealfall verlustfrei, aber meist keine 1:1-Zuordnung möglich.
  * inhaltliches mapping z.B. https://coli-conc.gbv.de/ für Klassifikationen
* XSLT
  * Programmiersprache zur Transformation von XML-Dokumenten (W3C Empfehlung, 1999)
  * Literaturempfehlung für Einstieg in XSLT: <https://programminghistorian.org/en/lessons/transforming-xml-with-xsl>
* Online-Tool: http://xsltransform.net oder https://www.freeformatter.com/xsl-transformer.html
* In Alma verwendbar 
    * um z.B. Briefe an Kunden zu gestalten: 
    * https://developers.exlibrisgroup.com/blog/alma-letters-xml-samples-for-working-on-xsl-customization/
    * https://github.com/Swiss-Library-Service-Platform/Alma-letters

![Borrowed_by_letter_in_preview_pane](https://hackmd.io/_uploads/Bk6mE99R1x.png)

*    oder für die Normalisierungregeln (Bibliomedia Import)

Note:
Viele Tools haben XSLT 1.0 Limitierungen 


#### Beispiele der Library of Congress (LoC)

* MARC21 zu DC: https://www.loc.gov/marc/marc2dc.html
* DC zu MARC21: https://www.loc.gov/marc/dccross.html

#### Transformation von DSpace DC zu MARC21

* XSL: https://www.loc.gov/standards/marcxml/xslt/DC2MARC21slim.xsl


#### Transformation von Context EAD zu MARC21 


* XSL: https://github.com/reeset/marcedit_xslt_files

Online-Tools wie xsltransform.net oder https://www.freeformatter.com/xsl-transformer.html scheitern hier mit der Fehlermeldung:

```
Error at xsl:import on line 4 column 43 
  XTSE0165: I/O error reported by XML parser processing
  file:/opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl:
  /opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl (No such file or directory)
```

Wir nutzen für diese Transformation eine selbstgeschriebene XSL in Jupyter: https://github.com/Rouven-Schabinger/bain-jupyter-codespaces/tree/main/xsl

Damit könnte man auch mehrere Datein bearbeiten (batch processing).
Wer eine GUI möchte kann auch das Tool MarcEdit (s.u.) nutzen, das mit komplexeren XSL umgehen kann und schon viele für den Bibliotheksbereich nützliche XSL-Scripte mitliefert.


### Übung:


Beispieldateien unter https://github.com/Rouven-Schabinger/bain-jupyter-codespaces/tree/main/example

1. Transformieren Sie DSpace DC zu MARC21 mit dem Online-Tool
2. Transformation von Context EAD zu MARC21 mit diesem Notebook *transformation.ipynb*
3. Schauen Sie sich die XLS im Ordner /xsl an. Was wird bei beiden auf MARC 245 gemappt?
4. Sind Sie zufrieden mit der EAD zu MARC Transformation?

### MarcEdit [optional]

 MarcEdit ist eine kostenlos nutzbare Software aber nicht Open Source (siehe [Lizenz](https://marcedit.reeset.net/marcedit-end-user-license-agreement))
* Sie ist die meistgenutzte Zusatzsoftware für die Arbeit mit MARC21.
* Offizielle Webseite: <https://marcedit.reeset.net>
* [Lehrmaterialien von Library Carpentry zu MarcEdit](https://librarycarpentry.org/lc-marcedit/)

#### Transformation von ArchivesSpace EAD zu MARC21 

* XML: https://github.com/felixlohmeier/bain-oai/raw/main/example/archivesspace-ead.xml als Datei auf der Festplatte speichern

* Button MARC Tools
* 1. Schritt:
  * Operation: EAD=>MARC
  * Open... archivesspace-ead.xml (dort unten auf all files wechseln)
  * Save as... archivesspace-ead.mrc
  * Character Encoding: UTF8
* 2. Schritt:
  * Operation: MARC21=>MARC21XML
  * Open... archivesspace-ead.mrc
  * Save as... archivesspace-marc.xml
  * Character Encoding: UTF8
* Konvertierung verlustbehaftet
* Ergebnis: https://github.com/felixlohmeier/bain-oai/raw/main/results/archivesspace-marc.xml




### Weitere Tools zur Metadatentransformation



Vergleich von OpenRefine mit anderen Tools:
* Merkmale von OpenRefine:
    * grafische Oberfläche: Transformationsergebnisse werden direkt sichtbar
    * Skriptsprachen (GREL, Jython, Clojure) für komplexe Transformationen
    * Schwerpunkt auf Datenanreicherung (Reconciliation)
* Alternative Software:
    * Jupyter und libraries wie pandas, lxml, [pymarc](https://pymarc.readthedocs.io) 
    * [Catmandu](https://librecat.org) (Perl)
    * [Metafacture](https://metafacture.org) (Java)
    * [MarcEdit](https://marcedit.reeset.net) (für MARC21)
* Siehe auch:
  * Handbuch "Processing MARC21" von Johann Rolschewski: https://jorol.github.io/processing-marc/
  * Viele Einrichtungen bieten Online Labs: 
      * [Deutsche Nationalbibliothek](https://www.dnb.de/DE/Professionell/Services/WissenschaftundForschung/DNBLab/dnblabTutorials.html?nn=849628) und [PDF](https://opus4.kobv.de/opus4-bib-info/frontdoor/index/index/searchtype/collection/id/17576/rows/100/start/421/docId/19497)
      * [ZB Lab](https://www.zb.uzh.ch/de/ueber-uns/zb-lab)


Zur Wahl der passenden Software:
* Generell gilt, dass die passende Software anhand des Anwendungsfalls gewählt werden sollte.
* In der Praxis wird oft die Software verwendet, die schon gut beherrscht wird. Das macht es manchmal sehr umständlich.
* Bei wiederholter Benutzung können komplexere Frameworks verwendet werden



## Exkurs: Externe Datenbank bei SLSP
  ![kuyjf3vea2hg34taa-horizontal_default_slate_blue](https://hackmd.io/_uploads/HynTqghayl.svg)
  
https://www.mongodb.com/

* Technologie:
    * Dokumentendatenbank
    * JSON-ähnliches Format (Vgl. https://pkiraly.github.io/2018/01/28/marc21-in-json/)
* Regelmäßige Datensicherung der NZ Daten sicherstellen / Datenautonomie
* Ausreichend Indizes erstellen, um
die Daten zu untersuchen und Massenkorrekturen zu ermöglichen
* momentan nur NZ ohne Bestand, wöchentlich
![image](https://hackmd.io/_uploads/HyJXsenTkx.png)


https://github.com/Swiss-Library-Service-Platform/oaiharvester
* Live Einblick in MongoDBCompass, Bsp. MMS ID 991033321219705501
    * Versionen
    * Fehler in Daten
    *  Problem mit Indexen:  *Ambiguous field name found in array (do not use numeric field names in embedded elements in an array)*
*  Interaktion mit Python
 ![image](https://hackmd.io/_uploads/HyuPTln6yl.png)
 * andere ETL-Prozesse: [FRED](https://zop.zb.uzh.ch/items/36b7c4a7-6862-4358-ae52-d9cf3242c316)

* Abschnitt im Handbuch IT in Bibliotheken:
https://it-in-bibliotheken.de/metadaten.html#etl-prozess

* Schwammigster Punkt
