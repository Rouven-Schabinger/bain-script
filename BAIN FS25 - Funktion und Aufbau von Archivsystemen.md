# BAIN FS25 - Funktion und Aufbau von Archivsystemen 




## Installation und Konfiguration von ArchivesSpace


### Einführung in ArchivesSpace

- Open-Source-Software für Archivinformationssysteme
- 400 zahlende [Mitglieder](http://archivesspace.org/community/whos-using-archivesspace/), woraus fast 5 Vollzeitstellen finanziert werden.
- Code bei GitHub: https://github.com/archivesspace/archivesspace
- ArchivesSpace ist institutionell verankert bei [Lyrasis](https://en.wikipedia.org/wiki/Lyrasis), einem internationalen "nonprofit" Bibliotheksnetzwerk vorrangig aus den USA. Es gibt auch weitere  Unternehmen, die dazu professionellen Support anbieten.

#### Funktionen

"What ASpace does and how do we use it" (aus Fortbildungsmaterialien der [NYU](https://guides.nyu.edu/ld.php?content_id=23461999))

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

#### Exkurs zur Systemadministration (optional)

Angenommen, wir haben bereits Koha auf unserem Server installiert. Gibt es Probleme, wenn wir zusätzlich ArchivesSpace installieren?

**Mögliche Konflikte**:
- Versionskonflikte: Unterschiedliche Versionen gemeinsamer Bibliotheken oder Abhängigkeiten können zu Problemen führen.
- Ressourcenkonflikte: Beide Systeme könnten um dieselben Serverressourcen (z.B. Arbeitsspeicher, CPU) konkurrieren.

**Best Practice**:
- Isolation: Jedes System sollte in einer eigenen Umgebung betrieben werden, um Konflikte zu vermeiden und die Sicherheit zu erhöhen. Dies kann durch Virtualisierung oder Containerisierung erreicht werden.

**Kompatibilität von Koha und ArchivesSpace**:
- Koha und ArchivesSpace sind dafür bekannt, gut zusammenzuarbeiten, da sie unterschiedliche Funktionen erfüllen (Koha für Bibliotheksmanagement, ArchivesSpace für Archivverwaltung). Daher ist es in vielen Fällen möglich, beide Systeme auf demselben Server zu installieren, solange die Ressourcen ausreichend sind und die Konfigurationen sorgfältig vorgenommen werden.

**Technische Details**:
- Programmiersprachen: Konflikte können auftreten, wenn die Systeme unterschiedliche Versionen derselben Programmiersprache (z.B. Java, PHP) benötigen.
- Datenbanken: Auch unterschiedliche Versionen von Datenbanken (z.B. MySQL, PostgreSQL) können zu Problemen führen.




### Installation ArchivesSpace

* Wir nutzen heute die Demo-Installation von ArchivesSpace
* Login im Staff Interface unter https://sandbox.archivesspace.org/staff
  * Username: `admin`
  * Password: `admin`
* Einen Codespace mit ArchivesSpace hatte der vorherige Dozent einmal erstellt, aber da funktioniert das "Public Interface" (noch) nicht: https://github.com/felixlohmeier/bain-archivesspace

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
- Weitere Optionen: Siehe technische Dokumentation https://docs.archivesspace.org/

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
* beim Aufruf einer Resource ist im Abschnitt "Related Accessions" eine Verknüpfung möglich oder direkt beim Erstellen einer Accession eine Ressource spawnen

### Übung

Übung: Datensätze erstellen

- Aufgabe: Erstellen Sie eigene Datensätze in der ArchivesSpace Sandbox. Erfinden Sie dazu sinnvolle Archivdaten oder suchen Sie sich Beispieldaten (z.B. im [Hochschularchiv der ETH](https://vls.hsa.ethz.ch/client/)).
- Ziel: Ihre Datensätze erscheinen in der öffentlichen Ansicht. Machen Sie einen Screenshot und laden Sie das Bild hier in das gemeinsame Dokument.
- Hinweis: Wenn Sie Hilfestellung benötigen, können Sie sich beim Vorgehen an der Übung der NYU orientieren: [Create Your Own Record](https://guides.nyu.edu/ld.php?content_id=23198351)

### Ergebnisse

Gruppe 1:
2025-03-12
![image](https://hackmd.io/_uploads/SkK_N112yg.png)
Gruppe 2: 
![Bildschirmfoto 2025-03-10 um 16.19.22](https://hackmd.io/_uploads/H1AZXF3okl.png)

Gruppe 3: 
Ressource 1-1-1-2 wurde erstellt und wird gefunden:
![grafik](https://hackmd.io/_uploads/Hk2_-F3oJg.png)
und sieht im Lesesaal aus wie folgt:
![grafik](https://hackmd.io/_uploads/SJD0-thoyl.png)



Gruppe 4:
![Screenshot](https://hackmd.io/_uploads/ryIFQt3sJe.png)

### Fragen

### Import und Export

ArchivesSpace bietet dateibasierten Import und Export in diversen Formaten (EAD, MARCXML, CSV) und auch eine OAI-PMH-Schnittstelle.

In den folgenden zwei Übungen werden wir EAD-Beispieldaten in ArchivesSpace importieren und anschließend in MARCXML exportieren.

#### Übung: Import

**Aufgabe**

- Beispieldaten: https://eadiva.com/2/sample-ead2002-files/ (laden Sie die als "a raw XML file" verlinkte Datei der "American Association of Industrial Editors" herunter)
- Aufgabe: Importieren Sie Beispieldaten im Format EAD in ArchivesSpace. Vergleichen Sie die Anzeige in ArchivesSpace mit der bei den Beispieldaten in EAD-XML
- Ziel: Dokumentieren Sie Ihre Erkenntnisse unten im gemeinsamen Dokument.
- Hinweis: Die Import-Funktion finden Sie etwas versteckt unter `Create` > `Background Job` > `Import Data`

#### Fragen / Erkenntnisse

* ...

#### Übung: Export

**Aufgabe** (optional)

- Aufgabe:
  1. Exportieren Sie die von Ihnen zuvor importierten Datensätze im Format MARCXML. Speichern Sie die Datei auf der Festplatte.
  2. Vergleichen Sie die exportierte MARCXML-Datei kurz mit den in ArchivesSpace vorhandenen Informationen. Ist der Export in MARCXML verlustfrei?
- Ziel: Dokumentieren Sie Ihre Erkenntnisse unten im gemeinsamen Dokument.
- Hinweis: Die Export-Funktion finden Sie etwas versteckt in der Button-Leiste bei der "Resource".

Note:

- Mappingtabellen als XLS (Stand 2013/2017, unklar ob aktuell) stellt ArchivesSpace auf der Webseite zur Verfügung: https://archivesspace.org/using-archivesspace/migration-tools-and-data-mapping
- Technische Dokumentation der Konvertierung in MARCXML (falls jemand die Proogrammiersprache Ruby können sollte): https://archivesspace.github.io/archivesspace/doc/MarcXMLBibBaseMap.html



#### Fragen / Erkenntnisse

* ...

#### Literatur zu ArchivesSpace

- Einführungsvideos: https://www.youtube.com/playlist?list=PL3cxupmXL7WiXaHnpVquPrUUiLiDAMhg0
- ArchivesSpace Wiki: https://archivesspace.atlassian.net/wiki/spaces/ADC/
- ArchivesSpace Manual for Local Usage at NYU: https://docs.google.com/document/d/11kWxbFTazB6q5fDNBWDHJxMf3wdVsp8cd7HzjEhE-ao/edit#

Note:

- Das Benutzerhandbuch von ArchivesSpace steht nur zahlenden Mitgliedern zur Verfügung. Bei Open-Source-Software suchen die Communities oft nach einem Zusatzvorteil für Mitglieder, weil die Software selbst ja kostenfrei erhältlich ist. Wirklich "open" ist diese Zurückhaltung von Informationen nicht so recht.





## Marktüberblick Archivsysteme 



- ArchivesSpace hat eine große Community in den USA
- Weitere Open-Source-Alternative: [Access to Memory (AtoM)](https://www.accesstomemory.org)
- Dienstleister in der Schweiz: [docuteam](https://www.docuteam.ch/atom-access-to-memory/)
-Für die Entwicklung von Grundsätzen für AtoM 3 gibt es eine “Foundation” https://accesstomemoryfoundation.org  verein
- AtoM 3 soll Records in Contexts (RiC) unterstützen
-AtoM 3 Design Principles https://docs.google.com/presentation/d/1hJJ8PUpV7YIbJZaWfU4hIMGU70hKR94-dPiUXKAAsFY/
- Der Markt in der Schweiz wird von den Produkten [scopeArchiv](https://www.scope.ch/de/produkteuebersicht/scopearchiv/) und [CMI AIS](https://cmiag.ch/akten-management/archivierung/ais/) (ehemals CMISTAR) dominiert.
- Für die Online-Präsentation von digitalisiertem Archivgut wird oft zusätzliche Software eingesetzt. Beispiele:
  - [E-Pics Plattform der ETH Zürich](https://www.e-pics.ethz.ch) (WordPress + Canto Cumulus)
  - [e-manuscripta.ch - Kooperative Präsentationsplattorm für handschriftliche Quellen](http://www.e-manuscripta.ch) (Visual Library)
  - [Smapshot](https://smapshot.heig-vd.ch/) Sehr cooles Projekt, um Bilder zu geolokalisieren, präsentieren und mit Metadaten anzureichern (Citizen Science).

## Unterschiede zwischen Bibliotheks- und Archivsystemen

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

## Sonstiges


- aber auch zunehmende **Konvergenz** von [GLAM](https://de.wikipedia.org/wiki/GLAM), externe Ressourcen in swisscovery (Bsp. ETH):
  - [E-Periodica](https://www.e-periodica.ch/) 
  - [E-Pics](https://www.e-pics.ethz.ch/de/home/)
  - [E-Rara](https://www.e-rara.ch/)
  - [Research Collection](https://www.research-collection.ethz.ch/)
  - [Videoportal](https://video.ethz.ch/)
  - [Materialarchiv](https://materialarchiv.ch/de/app-tablet/)
  - [Hochschularchiv Online](https://library.ethz.ch/publizieren-und-archivieren/archivieren/hochschularchiv-der-eth-zuerich.html)
  - [Max Frisch Archiv Online](http://maxfrischarchiv-online.ethz.ch/home/#/)
  - [Thomas Mann Archiv Online](http://www.online.tma.ethz.ch/home/)
  - [Thomas Mann Nachlassbibliothek](https://nb-web.tma.ethz.ch/)
  
- GLAMhack als Beispiel für einen [Hackathon](https://en.wikipedia.org/wiki/Hackathon): https://hack.glam.opendata.ch/event/12 z.B. Unveiling the Secrets of Zurich’s Nightly Visitors (1780-1818)"

