# BAIN FS26 - Zukunftstechnologien

## Quiz 

## Mini-Konferenz
![image](https://hackmd.io/_uploads/HkHKOA6bxe.png)


* ersten Hälfte des Blocks: Wahl eines Themas und dann Ausarbeitung

* Recherchieren Sie im Internet probieren Sie wenn möglich genenannte **Dienste/Projekte** aus
    * Literaturhinweise in BAIN
    * Webseiten
    * Fachartikel
    * Videos
    * GPTs (kritisch prüfen "Werbetextformulierungen") 
    * [FHNW Bib - Research Bar](https://moodle.fhgr.ch/course/index.php?categoryid=491 )

* Teilen Sie zuerst in der Gruppe die Arbeit unter sich auf

* Reflektieren Sie danach über Anknüpfungspunkte aus allen Lektionen (Z.B. Vortrag Herr Würtz) und diskutieren Sie in Ihrer Gruppe

* Wissenswiedergabe des Themas und kritischer Ausblick kann je nach Thema variieren:
    * **Was ist die Technologie? (z.B. Klärung zentraler Begriffe)** 
    * **Welche Anwendung(en)/Projekte gibt es schon im GLAM-Bereich?**
    * **Welche Risiken/Herausforderungen gibt es?**

* Erstellen Sie ein Präsentation mit einem Tool Ihrer Wahl (z.B. Powerpoint oder napkin.ai), die Folien laden wir nach der Sitzung in Moodle hoch.

* zweite Hälfte des Blocks: Präsentation 20 Minuten + 10 Minuten Diskussion

## Themen

###  Linked Open  Data und aktuelle Datenmodelle für Metadaten (BIBFRAME, RiC) 
**Leitfragen**:


* Welche Herausforderungen und Vorteile gibt es bei der Implementierung von BIBFRAME und RiC?

* Was sind die fünf Designprinzipien von LOUD und wie fördern sie die Nutzbarkeit von Daten? (Welche Rolle spielt JSON-LD in der Umsetzung von LOUD?)
* Welche Rolle spielen semantische Datenmodelle und Knowledge Graphs für die Vernetzung und Nachnutzung von Metadaten und wie kann man es mit KI kombinbieren?

**Erste Quellen:**

*BIBFRAME*
* BIBFRAME bei der Library of Congress:
    *  https://www.loc.gov/bibframe/
    * Gegenüberstellung BIBFRAME <-> MARCXML: https://id.loc.gov/tools/bibframe/comparebf-lccn/2018958785.xml
    * Model:
*![BIBFRAME Model](https://www.loc.gov/bibframe/docs/images/bf2-model.jpg)
    Quelle: https://www.loc.gov/bibframe/docs/bibframe2-model.html
    * Ontologie: https://id.loc.gov/ontologies/bibframe.html
    * Unterschiede zu MARC: <https://www.loc.gov/bibframe/faqs/#q04>
    * Aktuelles: https://www.loc.gov/bibframe/news/bibframe-update-jan2025.html
* [Präsentationen zu BIBFRAME auf der SWIB](https://www.google.com/search?q=site%3Ahttps%3A%2F%2Fswib.org+bibframe&sca_esv=69251213fe4ae3f6&sxsrf=AHTn8zqE2LvMi94onVdpFxBK4LvVQL1ObA%3A1747381832149&ei=SO4maL7sCNmE9u8P0P6JgQ4&ved=0ahUKEwi-sJHLwKeNAxVZgv0HHVB_IuAQ4dUDCBI&uact=5&oq=site%3Ahttps%3A%2F%2Fswib.org+bibframe&gs_lp=Egxnd3Mtd2l6LXNlcnAiHnNpdGU6aHR0cHM6Ly9zd2liLm9yZyBiaWJmcmFtZUjFD1C0CVjqDnABeAGQAQCYAXSgAZ4DqgEDNS4xuAEDyAEA-AEBmAICoAJ-wgIKEAAYsAMY1gQYR8ICBRAAGO8FwgIIEAAYogQYiQXCAggQABiABBiiBJgDAIgGAZAGCJIHAzEuMaAHygWyBwMwLjG4B3jCBwUwLjEuMcgHBg&sclient=gws-wiz-serp)


* BIBFRAME Must Die: https://scholarsphere.psu.edu/resources/fc19faee-70b9-44b3-9346-18e40a2cd990

*RiC*
* RiC Modell

![](https://raw.githubusercontent.com/ICA-EGAD/RiC-O/master/diagrams/diagrams_v0-2/RiC-CM-overview/diagram_RiC-CM-overview-RiC-v0-2.jpg)


* Ontologie https://www.ica.org/standards/RiC/ontology
* Beispieldateien: https://github.com/ICA-EGAD/RiC-O/tree/master/examples/examples_v0-2

RiC Tools:

 * Open-Source-Software [RiC-O Converter](https://archivesnationalesfr.github.io/rico-converter/en/)

* Einführungsartikel: David Gniffke (16.3.2020): Semantic Web und Records in Contexts (RiC). In: Archivwelt, 16/03/2020. <https://archivwelt.hypotheses.org/1982>


* Archival Linked Open Data (aLOD): <http://www.alod.ch>

 * Präsentationen der Abschlussveranstaltung: https://vsa-aas.ch/ressourcen/ensemen/veranstaltungen/
    * Präsentation zu Memobase: https://archiv.vsa-aas.ch/wp-content/uploads/2022/03/2022-03-25-Pr%C3%A4sentation-1-Daniel-Hess-VSA-Projektgruppe-ENSEMEN.pdf
    * Transformation von öffentlichen Daten im AIS nach RiC-O: https://archiv.vsa-aas.ch/wp-content/uploads/2022/03/2022-03-25-Pr%C3%A4sentation-3-Lambert-Kansy-VSA-Projektgruppe-ENSEMEN.pdf

*Linked Data*

* ausführlichere Einführung in LOD: https://slides.lobid.org/2022-05-06-lod-dipf
* Diskussion: https://metadaten.community/t/rdf-fuer-bibliographische-angaben/624 und https://metadaten.community/t/linked-open-data-dach-bibliotheken-eingeschlafen/533


* Linked Data Schnittstelle bei der ZB Zürich: https://data.zb.uzh.ch/map/books/data-map-der-zentralbibliothek-zurich/page/alma-linked-data

* Rekatalogisierung historischer Zettelkataloge mit LVLM: Ein Pilotprojekt der UB Basel zur automatisierten Metadatenextraktion: https://nbn-resolving.org/urn:nbn:de:0290-opus4-201564 

* Swiss Performing Arts Platform
example of LOD deployment by a small institution without an IT department: https://docs.google.com/presentation/d/1UKA2b5xRbpZVr8eodyko1z3yY4xqJCxHbFbO5jamRpk

* Anreicherung mit Normdaten für die Suche:
     * https://eth.swisscovery.slsp.ch/discovery/search?query=any,contains,escher&tab=discovery_network&search_scope=DiscoveryNetwork&vid=41SLSP_ETH:ETH&lang=en&offset=0
    ![image](https://hackmd.io/_uploads/H1jCvy0bll.png)



###  AI, z.B. Large Language Models (LLMs)
**Leitfragen**:
* Welche Einsatzmöglichkeiten gibt es für AI und LLMs in Bibliotheken und Archiven?
* Welche ethischen und sicherheitsrelevanten Aspekte müssen bei der Nutzung von AI und LLMs berücksichtigt werden?
* Welche Rolle spielen semantische Datenmodelle und Knowledge Graphs für die Vernetzung und Nachnutzung von Metadaten und wie kann man es mit KI kombinbieren?

**Erste Quellen**:
*  Primo Research Assistant: 
    *  https://knowledge.exlibrisgroup.com/Primo/Product_Documentation/020Primo_VE/Primo_VE_(English)/015_Getting_Started_with_Primo_Research_Assistant
    * Videovorführung: https://www.youtube.com/watch?v=3Wd0vk64uj0
    * mit edu-id testbar: https://slsp-network.primo.exlibrisgroup.com/discovery/login?vid=41SLSP_UZB:RA_test_UNION

    * Funktionsweise:
![image](https://hackmd.io/_uploads/B16Rm92-eg.png)

*  Clarivate Metadata Assistent: 
    *  https://knowledge.exlibrisgroup.com/Alma/Product_Documentation/010Alma_Online_Help_(English)/Metadata_Management/005Introduction_to_Metadata_Management/The_AI_Metadata_Assistant_in_the_Metadata_Editor 
    *  [in action](https://docs.google.com/presentation/d/1F4WORK584pKl48do61W0P9lRjzc4akb-/edit?usp=sharing&ouid=106252531505293612084&rtpof=true&sd=true)
    *  Demo: https://www.youtube.com/watch?v=Sh7hli0uE5A
* Themen: z.B. [RAG](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) und  [NER](https://en.wikipedia.org/wiki/Named-entity_recognition)

![image](https://hackmd.io/_uploads/B11Ek5Olfg.png)

* AI: Rethinking Search and Cataloguing [Slides](https://drive.google.com/file/d/1K9pts4lNubPgTSPgmbCmq_ex2E9hyUB_/view?usp=sharing)
* Kann man grob auch in einem belibigen GPT testen, Cover hochladen oder Titel + Autor eingeben und sagen erstelle mir eine Aufnahme in MARC
*  Open Research Knowledge Graph (ORKG): https://ask.orkg.org/

* Balnaves, Edmund, Bultrini, Leda, Cox, Andrew and Uzwyshyn, Raymond. New Horizons in Artificial Intelligence in Libraries, Berlin, Boston: De Gruyter Saur, 2025. https://doi.org/10.1515/9783111336435

* Archivierung von Unterlagen aus digitalen Systemen Tagung / Block 3: KI und der digitale Lesesaal: https://www.sg.ch/kultur/staatsarchiv/Spezialthemen-/auds/2025.html

* Artificial Intelligence for Libraries, Archives & Museums (AI4LAM): https://www.youtube.com/@ai4lam120/videos


## Community, Rückblick, Sonstiges
* Community
* Rückblick
* Sonstiges 
    * https://www.go-fair.org/fair-principles/
    * https://librarycarpentry.github.io/lc-spreadsheets/02-common-mistakes.html#common-spreadsheet-errors
    * https://www.sg.ch/news/sgch_allgemein/2026/05/internet-archive-switzerland-nimmt-arbeit-auf.html


## Organistatorisches


### Lerntagebücher





* Vorgaben  der Semesterinformation in Moodle


* Fragen zu Inhalt, Form oder Bewertungskriterien?


  * Fragen können gerne auch später noch per im Diskussion-Forum oder per E-Mail gestellt werden.


* Abgabe als eine PDF bis spätestens 03. Juli 23:59 Uhr in Moodle
### Evaluation

* zweiter Durchlauf, ca. 20 % angepasst (Alma-SLSP/jupyter/docuteam context)
* generelle Übereinstimmung mit Erwartungshaltung von erster Stunde


* gut: Praxisbezug / Fachkompetenz

**Verbesserungen**:
* Übungen zu schwierig
   --> Steigerung Übungsfreiheit vom Anfang des Kurses (exakte Anweisungen, Teilaufgaben a,b,c) bis zum Ende (eher offen, "testen Sie einige Paramater aus der Dokumentation") 
aber werde Beschreibungen nochmal überprüfen und Quellen verringern
   --> Vor- und Nachbereitung und etwas Vorwissen aus anderen Modulen aber notwendig

* Leistungsnachweis (fachfremd, unklar, Zeichenbeschränkung, Zwischenfazit)
--> Prüfungsform Lerntagebuch als Portfolio, Alternativen:
    * Projektarbeit 
    * praktische Prüfung 
    * Klausur mit oder ohne Hilfsmittel
    * mündliche Prüfung

generell:
   --> Methoden und Wissen auf andere IT-Bereiche übertragbar (Metadaten, ETL, APIs ...)
   --> Studienjahr 2026 wird Curriculum verändert und das Modul BAIN etwas anpasst

