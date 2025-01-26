# BAIN FS25 - Metadaten modellieren und Schnittstellen nutzen

* hier kommt alles aus den vorheringen Sessions zusammen

## Ausgangsdaten

![mermaid-2025-01-16-144111](https://hackmd.io/_uploads/Sk7h5c8wyl.png)


* Alma: MARCXML via OAI-PMH aus HPH Sandbox
* ArchivesSpace: EAD via OAI-PMH aus Demo-Installation
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
* Z39.50 ist sehr alt, aber immer noch im Einsatz. Meist wird das modernere SRU als Ergänzung angeboten. Das Schöne an SRU und OAI-PMH ist, dass die Anfragen als Internetadresse (URL) zusammengestellt werden können und direkt über den Browser ohne Zusatzsoftware aufrufbar sind.

### Metadaten über OAI-PMH harvesten mit Sickle

Vorbereitung:

Codespace aufrufen mit vorbereitetem Repository (als Juypterlab)
https://github.com/Rouven-Schabinger/bain-jupyter-codespaces


Aufgabe: Kürzel für Metadatenformat ermitteln und das Kommando zum Aufruf des Harvestings jeweils entsprechend anpassen und ausführen

#### Alma MARC21

* OAI-PMH Basisurl: https://slsp-hph-psb.alma.exlibrisgroup.com/view/oai/41SLSP_HPH/request
* Verfügbare Metadatenformate: https://slsp-hph-psb.alma.exlibrisgroup.com/view/oai/41SLSP_HPH/request?verb=ListMetadataFormats

```

```

#### ArchivesSpace EAD

* OAI-PMH Basisurl: https://sandbox.archivesspace.org/oai
* Verfügbare Metadatenformate: https://sandbox.archivesspace.org/oai?verb=ListMetadataFormats

```

```

#### DSpace OAI-DC

* OAI-PMH Basisurl: https://demo.dspace.org/oai/request
* Verfügbare Metadatenformate: https://demo.dspace.org/oai/request?verb=ListMetadataFormats

```

```

## Konvertierung

Beispieldateien unter https://github.com/Rouven-Schabinger/bain-jupyter-codespaces/tree/main/example

### XSLT Crosswalks

* Wir haben nun Daten in verschiedenen Formaten (MARC21-XML, EAD und DC) vorliegen.
* Nun werden wir diese einheitlich in MARC21-XML konvertieren.
* Crosswalks
  * Gängiger Begriff, um die Konvertierung von einem Metadatenstandard in einen anderen zu beschreiben.
  * Beispiel: Dublin Core zu MARC21.
  * Der "Crosswalk" beinhaltet Regeln wie Elemente und Werte zugeordnet werden (sog. Mapping).
  * Im Idealfall verlustfrei, aber meist keine 1:1-Zuordnung möglich.
  * inhaltliches mapping z.B. https://coli-conc.gbv.de/ für Klassifikationen
* XSLT
  * Programmiersprache zur Transformation von XML-Dokumenten (W3C Empfehlung, 1999)
  * Literaturempfehlung für Einstieg in XSLT: <https://programminghistorian.org/en/lessons/transforming-xml-with-xsl>
* Online-Tool: http://xsltransform.net

#### Beispiele der Library of Congress (LoC)

* MARC21 zu DC: https://www.loc.gov/marc/marc2dc.html
* DC zu MARC21: https://www.loc.gov/marc/dccross.html

#### Transformation von DSpace DC zu MARC21

* XSL: https://www.loc.gov/standards/marcxml/xslt/DC2MARC21slim.xsl


#### Transformation von ArchivesSpace EAD zu MARC21 (Versuch 1)


* XSL: https://github.com/reeset/marcedit_xslt_files

Online-Tools wie xsltransform.net scheitern hier mit der Fehlermeldung:

```
Error at xsl:import on line 4 column 43 
  XTSE0165: I/O error reported by XML parser processing
  file:/opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl:
  /opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl (No such file or directory)
```

utzen für diese Transformation das folgende eine selsbtgeschriebene XSL und Jupyter, damit könnte man auch mehrere Datein bearbeiten (batch processing).
Wer eine GUI möchte kann auch das Tool MarcEdit nutzen, das mit komplexeren XSL umgehen kann und schon viele für den Bibliotheksbereich nützliche XSL-Scripte mitliefert.

**Könnt ihr zuhause versuchen!**
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



### ETL-Prozess

Abschnitt im Handbuch IT in Bibliotheken:
https://it-in-bibliotheken.de/metadaten.html#datenverarbeitung

Beispiel des OPAC-NG-Projekts für das Deutsche Literaturarchiv Marbach
* Katalog: https://www.dla-marbach.de/katalog-beta/
* Informationen zum Projekt: https://wdv-teamwork.dla-marbach.de/projects/info-opac-ng-hauptprojekt/wiki
* Details zur Systemarchitektur: https://felixlohmeier.de/dla/systemarchitektur.html

### Weitere Tools zur Metadatentransformation

Beispiel für Metadaten-Management in der Praxis, hier beim Leibniz-Informationszentrum Wirtschaft (ZBW) in Hamburg:
* Infoseite: https://www.zbw.eu/de/ueber-uns/wissensorganisation/metadaten-management
* Videointerview mit Kirsten Jeude: https://www.youtube.com/watch?v=YwbRTDvt_sA

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
  * Prof. Magnus Pfeffer (2016): Open Source Software zur Verarbeitung und Analyse von Metadaten. Präsentation auf dem 6. Bibliothekskongress. <https://nbn-resolving.org/urn:nbn:de:0290-opus4-24490>

Zur Wahl der passenden Software:
* Generell gilt, dass die passende Software anhand des Anwendungsfalls gewählt werden sollte.
* In der Praxis wird oft die Software verwendet, die schon gut beherrscht wird. Das macht es manchmal sehr umständlich.
* Bei wiederholter Benutzung können komplexere Frameworks verwendet werden



## Aufgaben

Bis zum nächsten Termin 

* Beitrag zur Lehreinheit Schnittstellen (3000-4000 Zeichen)
