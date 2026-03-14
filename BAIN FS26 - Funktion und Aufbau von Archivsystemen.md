# BAIN FS26 - Funktion und Aufbau von Archivsystemen 

## Vortrag von Fabian Würtz
* Leitung Informatik [Schweizerisches Sozialarchiv](ch/)
* Bibliothek ist Teil von SLSP: https://libraries.swisscovery.help/?search=E19


## Wiederholung

* Quiz


## Archivsysteme: docuteam cosmos

* **docuteam** ist ein Schweizer Anbieter von Software und Dienstleistungen im Bereich Informationsmanagement und digitaler Archivierung. 


https://www.docuteam.ch/uber-uns/

* mit docuteam **cosmos** stellt die Firma eine modulare Softwarelösung für die digitale Langzeitarchivierung zur Verfügung, die sich am OAIS-Referenzmodell (ISO 14721) orientiert.


![image](https://hackmd.io/_uploads/SyuH2VGUWx.png)
[Quelle](https://www.docuteam.ch/wp-content/uploads/2024/07/docuteam_cosmos-de_v1-0.pdf)

* Der Betrieb ist in unterschiedlichen Varianten möglich, etwa als lokale Installation (On-Premises), als gehostete Lösung (Software as a Service) oder im Rahmen einer Dienstleistung, bei der der Archivbetrieb ganz oder teilweise ausgelagert wird.

**Module/Produkte (Auswahl):**

* docuteam packer / feeder
Bereitet Daten für die Archivierung vor und erstellt SIPs (Submission Information Packages) mit Metadaten. Workflow-Engine für kontrollierte Ingest-Prozesse (Datenübernahme, Migration, Validierung).

* docuteam box
Das digitale Archiv/Repository (magazin) selbst; zentrale Verwaltung und API-Schnittstelle. Baut auf Fedora auf (siehe Kapitel Repositorien)


* docuteam sirius
Virtueller Lesesaal zur Publikation und Recherche in den archivierten Beständen. 


### docuteam context
Archiv-Informations-System (AIS) zur Verzeichnung und Verwaltung der archivierten Daten, welches auf dem neuen Metadaten-Standard «Records in Contexts» (RiC) aufbaut.

Dokumentation: https://docs.docuteam.ch/context/




#### Funktionen

- Archivische Verzeichnung
Erfassung und Verwaltung von Archivbeständen, Serien, Dossiers und Einzelobjekten.

- Metadatenmanagement
Unterstützung strukturierter Metadaten nach archivischen Standards; Verwaltung von Beziehungen zwischen Einheiten.

- Verknüpfungen und Relationen
Abbildung von Beziehungen zwischen Records, Akteuren, Funktionen, Orten und Zeiträumen.

- Recherche und Suche
Suchfunktionen über Metadaten und Relationen, inkl. Filter- und Navigationsmöglichkeiten.

- Unterstützung von Akzessionen
Verwaltung von Zugängen und deren Weiterverarbeitung im Archivkontext.

- Anbindung an Ingest und Langzeitarchiv
Integration mit anderen Komponenten von docuteam cosmos (z. B. feeder, box) zur Übernahme und Referenzierung archivierter Objekte.

- Formulare und Konfiguration
Anpassbare Erfassungsformulare für unterschiedliche Verzeichnungskontexte und Anforderungen.

- Export und Schnittstellen
Export von Metadaten sowie Nutzung von APIs zur Weiterverarbeitung oder Publikation.



#### Metadaten in docuteam context

- Datenmodell auf Basis von RiC
Umsetzung des Standards Records in Contexts (RiC) mit graphbasierter Modellierung statt starrer Hierarchien.
Vgl. 
    - https://docs.docuteam.ch/context/use/records-hierarchy/
    - "Unter der Haube": Cypher-Abfragen direkt auf der Neo4j-Datenbank, Video: https://www.youtube.com/watch?v=ZmxP--HrTcg (französisch)
 
- Primäres Format ist JSON (vollständiger Export). Zusätzlich RDF und EAD (standardkonform, aber eingeschränkt). CSV-Import nur technisch, für Erschliessung meist ungeeignet.



### Zugriff auf das System

* Wir nutzen heute eine Demo-Installation von docuteam context
* Login  unter https://context2-cosmos.docuteam.cloud/268/records/

* **Republik der vergessenen Erinnerungen** ist ein Vorzeigearchiv (hier bitte nichts ändern)

* **Beispielarchiv**: hierunter kann man neue Datensätze anlegen



### Übung / Bedienung

- Wir nutzen nun die bereits diskutierten Grundlagen, um Datensätze in zu erschließen.
- Versuchen Sie bei der folgenden Gruppenarbeit intuitiv vorzugehen und tauschen Sie sich untereinander aus.
- Denken Sie an das Provenienzprinzip
- Dokumentation: https://docs.docuteam.ch/de/context/category/using
- Eigentlich noch Akzession (Dokumentation der Erwerbung) notwendig. Wegen vertraulichen Angaben oft nicht öffentlich.


Übung: Datensätze erstellen

- Aufgabe: Erstellen Sie eigene Datensätze. Erfinden Sie dazu sinnvolle Archivdaten oder suchen Sie sich Beispieldaten (z.B. im [SSA](https://www.findmittel.ch/))
- Dokumentieren Sie Fragen und Aufälligkeiten


### Ergebnisse

Gruppe 1:

Gruppe 2:


### Formulare und Validierung

Mit Formularen in docuteam context werden Entitäten (z. B. Records, Agents oder Places) erfasst, bearbeitet und strukturiert gespeichert, indem sie definieren, welche Felder angezeigt werden und wie die Daten im System gespeichert werden.

Was wird hier geprüft? (Stichwort Reguläre Ausdrücke)

```
{
  "sections": [
    {
      "content": [
        {
          "property": "comment",
          "fieldType": "input",
          "validationRegExp": "^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\\.[A-Za-z]{2,}$",
          "validationErrorText": {
            "de": "Bitte geben Sie eine gültige XXX ein.",
            "en": "Please enter a valid XXX."
          }
        }
      ]
    }
  ]
}
```


### Import und Export

docuteam context bietet dateibasierten Import und Export in diversen Formaten 
![image](https://hackmd.io/_uploads/SyEP8SfUWl.png)

![image](https://hackmd.io/_uploads/SyEVISMIZg.png)

(CNF: Configuration Format)



#### Übung: Export


**Aufgabe** 

- Aufgabe:
  1. Exportieren Sie die von Ihnen zuvor angelegten Datensätze im Format EAD XML. Speichern Sie die Datei auf der Festplatte.
  2. Vergleichen Sie die Angaben in context mit der Datei. Stimmt alles?


Note:
* EAD-Beispieldaten: https://eadiva.com/2/sample-ead2002-files/

#### Fragen / Erkenntnisse

* ...





### Exkurs zur Systemadministration

Angenommen, wir würden nicht mit Cloudsoftware arbeiten. Zu welchen Problemen kann es kommen?

Werden Fachanwendungen lokal auf eigener Infrastruktur betrieben, liegt die Verantwortung für Installation, Betrieb und Wartung bei der betreibenden Organisation. Bei der Installation mehrerer Systeme auf demselben Server können technische Wechselwirkungen auftreten.

**Typische Herausforderungen**
- **Abhängigkeiten und Versionen**: Anwendungen benötigen oft unterschiedliche Versionen von Bibliotheken, Laufzeitumgebungen oder Frameworks.
- **Ressourcennutzung**: Mehrere Systeme konkurrieren um begrenzte Serverressourcen wie Arbeitsspeicher, CPU oder Speicherplatz.

**Technische Details (Beispiele)**
- **Programmiersprachen und Laufzeitumgebungen**: Konflikte können entstehen, wenn Systeme unterschiedliche Versionen derselben Sprache oder Laufzeitumgebung benötigen (z. B. Java, PHP, Ruby, Python).
- **Datenbanken**: Probleme können auftreten, wenn Anwendungen verschiedene Datenbanksysteme oder unterschiedliche Versionen derselben Datenbank einsetzen (z. B. MySQL vs. PostgreSQL oder unterschiedliche Major-Versionen).

**Bewährte Praxis**
- **Isolation der Systeme**: Anwendungen sollten in getrennten Umgebungen betrieben werden, um Konflikte zu vermeiden und Wartung sowie Sicherheit zu vereinfachen (z. B. Virtualisierung oder Containerisierung).



## Marktüberblick Archivsysteme 

* **Open Source** Systeme: [ArchiveSpace](https://archivesspace.org/), 
    - 400 zahlende [Mitglieder](http://archivesspace.org/community/whos-using-archivesspace/), woraus mehrere Vollzeitstellen finanziert werden.
    - Code bei GitHub: https://github.com/archivesspace/archivesspace
    - ArchivesSpace ist institutionell verankert bei [Lyrasis](https://en.wikipedia.org/wiki/Lyrasis), einem internationalen "nonprofit" Bibliotheksnetzwerk vorrangig aus den USA. Es gibt auch weitere  Unternehmen, die dazu professionellen Support anbieten.
    - ArchivesSpace hat eine grosse Community in den USA
    - basiert auf den Standards [DACS](https://en.wikipedia.org/wiki/Describing_Archives:_A_Content_Standard), ISAD(G) und ISAAR(CPF)
    - Das Benutzerhandbuch von ArchivesSpace steht nur zahlenden Mitgliedern zur Verfügung. Bei Open-Source-Software suchen die Communities oft nach einem Zusatzvorteil für Mitglieder, weil die Software selbst ja kostenfrei erhältlich ist. Wirklich "open" ist diese Zurückhaltung von Informationen nicht so recht.


- sonst gibt es noch [Access to Memory (AtoM)](https://www.accesstomemory.org), AtoM 3 soll Records in Contexts (RiC) unterstützen. docuteam bietet Dienstleistungen an

- Der Markt in der Schweiz wird von den Produkten [scopeArchiv](https://www.scope.ch/de/produkteuebersicht/scopearchiv/) und [CMI AIS](https://cmiag.ch/akten-management/archivierung/ais/) (ehemals CMISTAR) dominiert.



- Für die Online-Präsentation von digitalisiertem Archivgut wird oft zusätzliche Software eingesetzt. Beispiele:
  - [E-Pics Plattform der ETH Zürich](https://www.e-pics.ethz.ch) (WordPress + Canto Cumulus)
  - [e-manuscripta.ch - Kooperative Präsentationsplattorm für handschriftliche Quellen](http://www.e-manuscripta.ch) (Visual Library)
  - [Smapshot](https://smapshot.heig-vd.ch/) Sehr cooles Projekt, um Bilder zu geolokalisieren, präsentieren und mit Metadaten anzureichern (Citizen Science).

## Unterschiede zwischen Bibliotheks- und Archivsystemen (Wiederholung)

- Bibliothek
  - (Massen-)Medium, Benutzerinteraktion (Ausleihe)
  - Software medienzentriert
  - Metadatenformat: MARC21, zukünftig BIBFRAME
  - Frühe Digitalisierung imitiert oft physische Vorgänge (vgl. Imagekataloge)
- Archiv
  - Entstehungszusammenhang, eher stehender, unikaler Bestand (Nutzung auf Anfrage)
  - Software orientiert sich an analogen Findmitteln
  - Metadatenformat: EAD, zukünftig RiC



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

## Lerntagebuch

* **Pflicht(!)**-Abgabe bis 02.04.2026 23:59 Uhr
* ich habe Ferien = abwesend (31.03.2026 - 10.04.2026)


## Sonstiges

* Arbeitskreis "Archivierung von Unterlagen aus digitalen Systemen (AUdS)" ist ein Netzwerk von Archivarinnen und Archivaren aus öffentlichen Archiven: https://www.sg.ch/kultur/staatsarchiv/Spezialthemen-/auds.html

* Tobias Wildi: Normen und Standards als Synergiepotentiale in der digitalen Archivierung: https://www.docuteam.ch/wp-content/uploads/2021/04/Artikel_Arbido_2-2012_Wildi.pdf
