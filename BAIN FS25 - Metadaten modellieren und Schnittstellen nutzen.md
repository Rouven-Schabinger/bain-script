---
title: BAIN FS25 - Metadaten modellieren und Schnittstellen nutzen

---

# BAIN FS25 - Metadaten modellieren und Schnittstellen nutzen



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

### Metadaten über OAI-PMH harvesten mit VuFindHarvest

Vorbereitung:

1. Codespace aufrufen mit vorbereitetem Repository
https://github.com/felixlohmeier/bain-oai
2. Abwarten bis "postCreateCommand" abgeschlossen ist und das Terminal erscheint
3. In das Verzeichnis von VuFindHarvest wechseln

```
cd vufindharvest-5.1.0
```

Aufgabe: Kürzel für Metadatenformat ermitteln und das Kommando zum Aufruf des Harvestings jeweils entsprechend anpassen und ausführen

#### Koha MARC21

* Vorab: Koha Administrationsoberfläche aufrufen und OAI-PMH aktivieren
* OAI-PMH Basisurl: https://catalog.bywatersolutions.com/cgi-bin/koha/oai.pl
* Verfügbare Metadatenformate: https://catalog.bywatersolutions.com/cgi-bin/koha/oai.pl?verb=ListMetadataFormats

```
php bin/harvest_oai.php --url=https://catalog.bywatersolutions.com/cgi-bin/koha/oai.pl --metadataPrefix=oai_dc test-koha
```

#### ArchivesSpace EAD

* OAI-PMH Basisurl: https://sandbox.archivesspace.org/oai
* Verfügbare Metadatenformate: https://sandbox.archivesspace.org/oai?verb=ListMetadataFormats

```
php bin/harvest_oai.php --url=https://sandbox.archivesspace.org/oai --metadataPrefix=oai_dc test-archivesspace
```

#### DSpace OAI-DC

* OAI-PMH Basisurl: https://demo.dspace.org/oai/request
* Verfügbare Metadatenformate: https://demo.dspace.org/oai/request?verb=ListMetadataFormats

```
php bin/harvest_oai.php --url=https://demo.dspace.org/oai/request --metadataPrefix=oai_dc test-dspace
```

## Konvertierung

Beispieldateien unter https://github.com/felixlohmeier/bain-oai/tree/main/example

### XSLT Crosswalks

* Wir haben nun Daten in verschiedenen Formaten (MARC21-XML, EAD und DC) vorliegen.
* Nun werden wir diese einheitlich in MARC21-XML konvertieren.
* Crosswalks
  * Gängiger Begriff, um die Konvertierung von einem Metadatenstandard in einen anderen zu beschreiben.
  * Beispiel: Dublin Core zu MARC21.
  * Der "Crosswalk" beinhaltet Regeln wie Elemente und Werte zugeordnet werden (sog. Mapping).
  * Im Idealfall verlustfrei, aber meist keine 1:1-Zuordnung möglich.
* XSLT
  * Programmiersprache zur Transformation von XML-Dokumenten (W3C Empfehlung, 1999)
  * Literaturempfehlung für Einstieg in XSLT: <https://programminghistorian.org/en/lessons/transforming-xml-with-xsl>
* Online-Tool: http://xsltransform.net

#### Beispiele der Library of Congress (LoC)

* MARC21 zu DC: https://www.loc.gov/marc/marc2dc.html
* DC zu MARC21: https://www.loc.gov/marc/dccross.html
  * XSL: https://www.loc.gov/standards/marcxml/xslt/DC2MARC21slim.xsl

#### Transformation von DSpace DC zu MARC21

* Tool: http://xsltransform.net oder https://www.freeformatter.com/xsl-transformer.html
* XML: https://github.com/felixlohmeier/bain-oai/raw/main/example/dspace-oai-dc.xml
* XSL: https://www.loc.gov/standards/marcxml/xslt/DC2MARC21slim.xsl
* Ergebnis: https://raw.githubusercontent.com/felixlohmeier/bain-oai/main/results/dspace-oai-marc.xml

#### Transformation von ArchivesSpace EAD zu MARC21 (Versuch 1)

* XML: https://github.com/felixlohmeier/bain-oai/raw/main/example/archivesspace-ead.xml
* XSL: https://github.com/reeset/marcedit_xslt_files

Online-Tools wie xsltransform.net scheitern hier mit der Fehlermeldung:

```
Error at xsl:import on line 4 column 43 
  XTSE0165: I/O error reported by XML parser processing
  file:/opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl:
  /opt/xsltransform/test-1.2.4/MARC21slimUtils.xsl (No such file or directory)
```

Wir nutzen für diese Transformation das folgende Tool MarcEdit, das mit komplexeren XSL umgehen kann und schon viele für den Bibliotheksbereich nützliche XSL-Scripte mitliefert.

### MarcEdit

 MarcEdit ist eine kostenlos nutzbare Software aber nicht Open Source (siehe [Lizenz](https://marcedit.reeset.net/marcedit-end-user-license-agreement))
* Sie ist die meistgenutzte Zusatzsoftware für die Arbeit mit MARC21.
* Offizielle Webseite: <https://marcedit.reeset.net>
* [Lehrmaterialien von Library Carpentry zu MarcEdit](https://librarycarpentry.org/lc-marcedit/)

#### Transformation von ArchivesSpace EAD zu MARC21 (Versuch 2)

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


## Nachtrag zu Metadaten modellieren und Schnittstellen nutzen

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
    * [Catmandu](https://librecat.org) (Perl)
    * [Metafacture](https://metafacture.org) (Java)
    * [MarcEdit](https://marcedit.reeset.net) (für MARC21)
* Siehe auch:
  * Handbuch "Processing MARC21" von Johann Rolschewski: https://jorol.github.io/processing-marc/
  * Prof. Magnus Pfeffer (2016): Open Source Software zur Verarbeitung und Analyse von Metadaten. Präsentation auf dem 6. Bibliothekskongress. <https://nbn-resolving.org/urn:nbn:de:0290-opus4-24490>

Zur Wahl der passenden Software:
* Generell gilt, dass die passende Software anhand des Anwendungsfalls gewählt werden sollte.
* In der Praxis wird oft die Software verwendet, die schon gut beherrscht wird. Das macht es manchmal sehr umständlich.
* Wer eine generische Programmiersprache wie Python gut beherrscht, kommt auch damit zum Ziel. Für Python gibt es übrigens eine Library für MARC21: https://pymarc.readthedocs.io


## Aufgaben

Bis zum nächsten Termin (21.05.):

* Beitrag zur Lehreinheit Schnittstellen (3000-4000 Zeichen)
