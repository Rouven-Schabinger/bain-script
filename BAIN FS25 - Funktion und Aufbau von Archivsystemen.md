---
title: BAIN FS25 - Funktion und Aufbau von Archivsystemen

---

# BAIN FS25 - Funktion und Aufbau von Archivsystemen 


Alle, die den Link zu diesem Dokument kennen, können es bearbeiten.

Link zur Teilnahme via WebEx: 

<- Agenda


## Metadatenstandards in Archiven: ISAD(G) und EAD

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

- Um Normdateien verzeichnen zu können, wurde später ein ergänzender Standard "International Standard Archival Authority Record for Corporate Bodies, Persons, and Families" - kurz [ISAAR(CPF)](https://de.wikipedia.org/wiki/ISAAR(CPF)) verabschiedet. Dieser wird in der Praxis wegen dem Zusatzaufwand bei der Erschließung jedoch nur selten verwendet.
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
## Marktüberblick Archivsysteme (Hr. Gasser)

- ETH, virtueller Lesesaal

- ArchivesSpace hat eine große Community in den USA
- Weitere Open-Source-Alternative: [Access to Memory (AtoM)](https://www.accesstomemory.org)
    - Dienstleister in der Schweiz: [docuteam](https://www.docuteam.ch/atom-access-to-memory/)
- Der Markt in der Schweiz wird von den Produkten [scopeArchiv](https://www.scope.ch/de/produkteuebersicht/scopearchiv/) und [CMI AIS](https://cmiag.ch/akten-management/archivierung/ais/) (ehemals CMISTAR) dominiert.
- Für die Online-Präsentation von digitalisiertem Archivgut wird oft zusätzliche Software eingesetzt. Beispiele:
  - [E-Pics Plattform der ETH Zürich](https://www.e-pics.ethz.ch) (WordPress + Canto Cumulus)
  - [e-manuscripta.ch - Kooperative Präsentationsplattorm für handschriftliche Quellen](http://www.e-manuscripta.ch) (Visual Library)
  - [Smapshot](https://smapshot.heig-vd.ch/) Sehr cooles Projekt, um Bilder zu geolokalisieren, präsentieren und mit Metadaten anzureichern (Citizen Science).

### Unterschiede zwischen Bibliotheks- und Archivsystemen

- Bibliothek
  - (Massen-)Medium, Benutzerinteraktion (Ausleihe)
  - Software medienzentriert
  - Metadatenformat: MARC21, zukünftig BIBFRAME
  - Frühe Digitalisierung imitiert oft physische Vorgänge (vgl. Imagekataloge)
- Archiv
  - Entstehungszusammenhang, eher stehender, unikaler Bestand (Nutzung auf Anfrage)
  - Software orientiert sich an analogen Findmitteln
  - Metadatenformat: EAD, zukünftig RiC

Note:
- Herausforderung: Datenaustausch zwischen den Systemen (kommen wir später darauf zurück)
- aber auch zunnehmnde **Konvergenz**, externe Ressourcen in swisscovery (Bsp. ETH):
  - [E-Periodica](https://www.e-periodica.ch/) 
  - [E-Pics](https://www.e-pics.ethz.ch/de/home/)
  - [E-Rara](https://www.e-rara.ch/)
  - [Research Collection](https://www.research-collection.ethz.ch/)
  - [Videoportal](https://video.ethz.ch/)
  - [Materialarchiv](https://materialarchiv.ch/de/app-tablet/)
  - [Hochschularchiv Online](https://library.ethz.ch/publizieren-und-archivieren/archivieren/hochschularchiv-der-eth-zuerich.html)
  - [Max Frisch Archiv Online](http://maxfrischarchiv-online.ethz.ch/home/#/)
  - [Thomas Mann Archiv Online](http://www.online.tma.ethz.ch/home/)
  - [Thomas Mann Nachlassbibliothek]([details](https://nb-web.tma.ethz.ch/))
- Beispiel für "Umfang" in verschiedenen Metadatenstandards: 
Schabinger, R. (2023). Does size matter? Quality assessment of the size property in research data repositories [Zenodo]. [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.8192783.svg)](https://doi.org/10.5281/zenodo.8192783)
- GLAMhack: https://hack.glam.opendata.ch/event/12 z.B. Nachtzedel



## Installation und Konfiguration von ArchivesSpace


### Einführung in ArchivesSpace

- Open-Source-Software für Archivinformationssysteme
- 400 zahlende [Mitglieder](http://archivesspace.org/community/whos-using-archivesspace/), woraus fast 5 Vollzeitstellen finanziert werden.
- Code bei GitHub: https://github.com/archivesspace/archivesspace
- ArchivesSpace ist institutionell verankert bei [Lyrasis](https://en.wikipedia.org/wiki/Lyrasis), einem internationalen "nonprofit" Bibliotheksnetzwerk vorrangig aus den USA. Es gibt auch zwei weitere Unternehmen, die dazu professionellen Support anbieten.

#### Funktionen

"What ASpace does and how do we use it" (aus Fortbildungsmaterialien der NYU

- System of record for archival materials. Not everything is public, or open to staff, nor is it intended to be.
- Perform core archival functions: accessioning, arrangement and description
- Aid in public services
- Record and report location holdings information; stacks management
- Manage digital objects
- Produce access tools
- Statistics gathering, prioritization, holistic planning
- Contribute to various interdepartmental processes (preservation and digitization)

#### Metadaten in ArchivesSpace

- basiert auf den Standards [DACS](https://en.wikipedia.org/wiki/Describing_Archives:_A_Content_Standard), ISAD(G) und ISAAR(CPF)
- unterstützt Import/Export in EAD, MARCXML und METS/MODS (Standard für Digitalisate: https://pro.deutsche-digitale-bibliothek.de/glossar/metsmods-format)

### Installation ArchivesSpace

* Wir nutzen heute die Demo-Installation von ArchivesSpace
* Login im Staff Interface unter https://sandbox.archivesspace.org/staff
  * Username: `admin`
  * Password: `admin`
* Einen Codespace mit ArchivesSpace hatte ich schon einmal erstellt, aber da funktioniert das "Public Interface" (noch) nicht: https://github.com/felixlohmeier/bain-archivesspace

### Grundkonfiguration ArchivesSpace

#### Repository anlegen

Menüpunkt System / Manage Repositories

Dort nutzen Sie den Button `Create Repository` um ihr Repository anzulegen.

- Notwendig sind zunächst nur `Repository Short Name` und `Repository Name`.
- Die Checkbox `Publish?` definiert, ob die Daten im "public interface" unter https://sandbox.archivesspace.org erreichbar sind.

#### Konfigurationsmöglichkeiten

- Spracheinstellung
  - Konfiguration: über Preferences (Global / Repository / User)
  - Sprachdateien: https://github.com/archivesspace/archivesspace/tree/master/common/locales
- Weitere Optionen: Siehe technische Dokumentation https://archivesspace.github.io/tech-docs/

### Bedienung

- Wir nutzen nun die zuvor diskutierten Grundlagen, um Datensätze in ArchivesSpace zu erschließen.
- Versuchen Sie bei der folgenden Gruppenarbeit intuitiv vorzugehen und tauschen Sie sich untereinander aus.
- Denken Sie an das Provenienzprinzip. Jede Ressource, die Sie verzeichnen wollen, benötigt zunächst Informationen zur Herkunft (Akzession).

#### Begrifflichkeiten

- [Accession](https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit#heading=h.qp2gyscl8fra): Dokumentation der Erwerbung, wegen vertraulichen Angaben oft nicht öffentlich
- [Resource](https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit#heading=h.jvn83ztmj4y4): Zentraler Nachweis auf der obersten Ebene der Verzeichnungsstufen, zum Beispiel zu einem Nachlass (kann aber auch direkt zum Objekt sein, wenn die Resource nur eine Verzeichnungsstufe hat)
- [Archival Object](https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit#heading=h.nscr859g1snm): Nachweis von Objekten auf weiteren Verzeichnungsstufen (Bestand/Fonds, Serie/Series, Akte/File, Einzelstück/Item). Sie werden über "Add Child" an vorhandene Resources gehängt.

Note:

* Verlinkte Begriffe führen zum [ArchivesSpace Manual for Local Usage at NYU](https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit), weil das offizielle Handbuch nur für Mitglieder zugänglich ist.
* beim Aufruf einer Resource ist im Abschnitt "Related Accessions" eine Verknüpfung möglich

### Übung

Übung: Datensätze erstellen

- Aufgabe: Erstellen Sie eigene Datensätze in der ArchivesSpace Sandbox. Erfinden Sie dazu sinnvolle Archivdaten oder suchen Sie sich Beispieldaten (z.B. im [Hochschularchiv der ETH](http://archivdatenbank-online.ethz.ch)).
- Ziel: Ihre Datensätze erscheinen in der öffentlichen Ansicht. Machen Sie einen Screenshot und laden Sie das Bild hier in das gemeinsame Dokument.
- Hinweis: Wenn Sie Hilfestellung benötigen, können Sie sich beim Vorgehen an der Übung der NYU orientieren: [Create Your Own Record](https://guides.nyu.edu/ld.php?content_id=23198351)

### Ergebnisse

Gruppe 1: Nicole, Morena, Sandra, Yara
![](https://pad.gwdg.de/uploads/2bfdf568-f545-482f-8e30-aa0a571a17c1.png)


Gruppe 2: Corina, Elena, Jonas, Rebecca
![](https://pad.gwdg.de/uploads/d2609d3c-975e-40c9-a31c-700cb57fe838.png)



Gruppe 3: Eva, Martina, Nina![](https://pad.gwdg.de/uploads/1f7bcfcd-65ba-40ed-ab87-c706a18c0cb0.png)



Gruppe 4:


### Fragen

- ![](https://pad.gwdg.de/uploads/6c953541-ba82-4997-8e02-92b9734cfe18.png)
Beim Erstellen des Datensatzes konnten wir Restrictions hinzufügen, jedoch gab es zwei Checkboxen. Werden die Restrictions erst angewendet wenn die obere Checkbox angewählt wird und die untere gibt nur an, dass Restrictions vorhanden sind? Oder treten die Restrictions bereits in Kraft mit dem Anwählen der unteren Checkbox? -> Was genau ist der Unterschied zwischen den beiden Boxen? (Wir haben uns nicht wirklich getraut es auszuprobieren...)
  - Das "Restrictions apply" verstehe ich als Überordnung. Nach Access Restrictions (Zugänglichkeit öffentlich oder vertraulich) gibt es darunter auch noch Usage Restrictions (Benutzung uneingeschränkt, nur unter Aufsicht, für die Benutzung gesperrt usw.). Restrictions Apply könnte wohl markiert werden wenn eins von beiden zutrifft.
  - Genau weiß ich es aber mangels kostenfreier Dokumentation nicht ;-)
- ![](https://pad.gwdg.de/uploads/943e3b76-2a1e-44e7-aa66-b4c413d05d76.png)
Es gibt hier zweimal Collection, ist das ein Konfigurationsfehler?
  - Ja, das sieht mir nach einem Bug aus. Hier ist kontrolliertes Vokabular hinterlegt und da dürfte es "Collection" eigentlich nur einmal geben.

Kann man diese rote Meldung dauerhaft abschalten (vielleicht ist das nicht erlaubt/gewünscht?)?
![](https://pad.gwdg.de/uploads/67901ff1-db8d-4954-900c-8043d4a6b26a.png)
- ja: das ist eine Systemnachricht, die man einstellen kann. Man kann sie auch deaktivieren.

Der Workflow von der Accession zur Ressource ist uns nicht klar. Wir haben eine [Accession](https://sandbox.archivesspace.org/repositories/14/accessions/13) angelegt. Konnten diese dann für die Erstellung der [Ressource](https://sandbox.archivesspace.org/repositories/14/resources/25) nicht nachnutzen. 
- beim Erstellen der Ressource auf die Accession verlinken über "Related Accessions". Damit wird eine Verlinkung zwischen beiden Datensätzen erstellt.
- eine andere (bessere) Möglichkeit: bei der Accession mit "Spawn" eine Ressource erstellen. So werden die bereits eingegebenen Metadaten übernommen und müssen nicht nochmals eingegben werden. 

Nur ein Kommentar: diese Suchergebnisse sehen wirklich toll aus (Ordnung, Übersicht, anklickbar):
![](https://pad.gwdg.de/uploads/b631fe09-a8e0-4b8e-b3b7-10fd63133d4f.png)


### Import und Export

ArchivesSpace bietet dateibasierten Import und Export in diversen Formaten (EAD, MARCXML, CSV) und auch eine OAI-PMH-Schnittstelle.

In den folgenden zwei Übungen werden wir EAD-Beispieldaten in ArchivesSpace importieren und anschließend in MARCXML exportieren.

#### Übung: Import

**Aufgabe (10 Minuten)**

- Beispieldaten: https://eadiva.com/2/sample-ead2002-files/ (laden Sie die als "a raw XML file" verlinkte Datei der "American Association of Industrial Editors" herunter)
- Aufgabe: Importieren Sie Beispieldaten im Format EAD in ArchivesSpace. Vergleichen Sie (ganz grob) die Anzeige in ArchivesSpace mit der bei den Beispieldaten verlinkten HTML-Ansicht.
- Ziel: Dokumentieren Sie Ihre Erkenntnisse unten im gemeinsamen Dokument.
- Hinweis: Die Import-Funktion finden Sie etwas versteckt unter `Create` > `Background Job` > `Import Data`

#### Fragen / Erkenntnisse

* ...

#### Übung: Export

**Aufgabe (10 Minuten)**

- Aufgabe:
  1. Exportieren Sie die von Ihnen zuvor importierten Datensätze im Format MARCXML. Speichern Sie die Datei auf der Festplatte.
  2. Vergleichen Sie die exportierte MARCXML-Datei kurz mit den in ArchivesSpace vorhandenen Informationen. Ist der Export in MARCXML verlustfrei?
- Ziel: Dokumentieren Sie Ihre Erkenntnisse unten im gemeinsamen Dokument.
- Hinweis: Die Export-Funktion finden Sie etwas versteckt in der Button-Leiste bei der "Resource".

Note:

- Mappingtabellen als XLS (Stand 2013/2017, unklar ob aktuell) stellt ArchivesSpace auf der Webseite zur Verfügung: https://archivesspace.org/using-archivesspace/migration-tools-and-data-mapping
- Technische Dokumentation der Konvertierung in MARCXML (falls jemand die Proogrammiersprache Ruby können sollte): https://archivesspace.github.io/archivesspace/doc/MarcXMLBibBaseMap.html

Export mit Struktur in EAD. Beispieldatensatz: https://sandbox.archivesspace.org/staff/resources/17


#### Fragen / Erkenntnisse

* ...

#### Literatur zu ArchivesSpace

- Einführungsvideos: https://www.youtube.com/playlist?list=PL3cxupmXL7WiXaHnpVquPrUUiLiDAMhg0
- ArchivesSpace Wiki: https://archivesspace.atlassian.net/wiki/spaces/ADC/
- ArchivesSpace Manual for Local Usage at NYU: https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit#

Note:

- Das Benutzerhandbuch von ArchivesSpace steht nur zahlenden Mitgliedern zur Verfügung. Bei Open-Source-Software suchen die Communities oft nach einem Zusatzvorteil für Mitglieder, weil die Software selbst ja kostenfrei erhältlich ist. Wirklich "open" ist diese Zurückhaltung von Informationen nicht so recht.


## Aufgabe bis zum nächsten Termin

* Eintrag im Lerntagebuch zur Lehreinheit Archivsysteme



