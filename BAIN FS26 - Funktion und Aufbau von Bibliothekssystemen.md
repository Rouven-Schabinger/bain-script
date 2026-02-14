# BAIN FS26 - Funktion und Aufbau von Bibliothekssystemen



## Wiederholung

* Vorstellung
* Praxiserfahrungen: Teilweise Software / Berufserfahrung vorhanden: gerne einbringen!
* Erwartungen
    *  grosse Übereinstimmun bei Inhalten, Erwartung und IT-Kenntnissen
    *  Ich: Verallgemeinerung von Bibliotheks- und Archivsoftware über die eigene Branche hinaus auf allgemeine IT-Fragestellungen soweit möglich.
* Organisatorisches: Termine, Leistungsnachweis
    * Lerntagebücher?
* Technische Grundlagen: **QUIZ**
* Exkurs zu Regular Expressions: https://regex101.com
  * Auch dazu gibt es übrigens eine Library Carpentry Lesson  https://librarycarpentry.org/lc-data-intro/01-regular-expressions.html

## Agenda
* Metadatenstandards in Bibliotheken (MARC21)
* SLSP
* Alma Import



## Metadatenstandards in Bibliotheken (MARC21)



* MARC21: International verbreiteter Metadaten-Standard, begründet von der Library of Congress 1999: <https://www.loc.gov/marc/bibliographic/>
* Hat [eigenes Binärformat](http://format.gbv.de/marc/iso) (.mrc), gibt's aber auch [als XML](http://format.gbv.de/marc/xml) und damit sind allgemeine XML-Tools darauf anwendbar
* wegen unterschiedlicher Katalogisierungsregeln und der Möglichkeit eigene Felder zu belegen, weicht die Verwendung international und auch nach Institution [stark vom vermeintlichen Standard ab](https://docs.google.com/presentation/d/e/2PACX-1vRU4J_rln00UVD7pNPT0_02NOad0HfSk_UKqRI0v29y8QkMAplEDlyjc0Ot_VE_paV6WBW29Fh_V-iN/pub?start=false&loop=false&delayms=3000#slide=id.g574306292a_0_35)
* Alma und alle anderen grossen Bibliothekssysteme basieren auf MARC21 oder unterstützen es als Austauschformat
* wird zukünftig voraussichtlich von [BIBFRAME](http://format.gbv.de/bibframe), einem Datenmodell basierend auf [RDF](http://format.gbv.de/rdf), abgelöst. Vgl. Tansformationsprozess
    * aktuell für Alma im Februar Release: [LOD Editor](https://www.youtube.com/watch?v=cJJCxjCQmqs)
* MARC ist recordbasiert
* Comic zu Standards: https://xkcd.com/927/ vgl. [MARC must die](https://hangingtogether.org/marc-must-die-15-years-on/)
### Übung: Vergleich MARC21 und Dublin Core

* Dublin Core ist ein Standard, der als kleinster gemeinsamer Nenner gilt
    * geht über die Bibliothekswelt hinaus
* Wir beziehen die Daten über die SRU-Schnittstelle von swisscovery (auf das Thema Schnittstellen und SRU gehen wir an einem anderen Tag noch ein)

**Aufgabe 1:** Laden Sie über die folgenden Links Daten über die SRU-Schnittstelle von swisscovery einmal im Format MARC21 und einmal im Format Dublin Core und vergleichen Sie diese.

* MARC21: https://swisscovery.slsp.ch/view/sru/41SLSP_NETWORK?version=1.2&operation=searchRetrieve&query=title=einstein&recordSchema=marcxml
* Dublin Core: https://swisscovery.slsp.ch/view/sru/41SLSP_NETWORK?version=1.2&operation=searchRetrieve&query=title=einstein&recordSchema=dc

**Vorabinfo zu swisscovery:**

- Der Katalog swisscovery beinhaltet die Daten der an SLSP teilnehmenden Bibliotheken.
- Der gemeinsame Katalog ermöglicht eine übergreifende Suche, gleichzeitig bietet swisscovery auch Schnittstellen an, über welche Metadaten der teilnehmenden Institutionen zentral bezogen werden können.
- Siehe auch: [Nutzung SLSP-Metadaten](https://slsp.ch/metadaten/), [Dokumentation der SRU-Schnittstelle von ALMA](https://developers.exlibrisgroup.com/alma/integrations/sru/)

**Aufgabe 2:**

* Ergänzen Sie Ihre praktischen Erkenntnisse durch Benutzen eines KI-Tools wie Le Chat Mistral zum Vergleich der zwei Metadatenformate. Stimmt alles?


### Erkenntnisse? Fragen?

* 


### Regelwerk vs. Datenformat

* Ein Regelwerk bildet die *theoretische* Grundlage für die Katalogisierung. Es definiert, wie eine Ressource zu beschreiben ist. Dazu gehören in der Regel inhaltliche Kategorien und normierte Vokabulare.
    * Functional Requirements for Bibliographic Records (FRBR) und Resource Description and Access (RDA) sind Regelwerke
* Ein Datenformat erlaubt die *praktische* Repräsentation eines Katalogisats. Es definiert, wie Informationen zu kodieren sind. Dazu gehören Datenstrukturen und -typen.
    * MARC21 und BIBFRAME sind Datenformate
* Regelwerke und Datenformate ergänzen einander und sind nicht immer trennscharf zu unterscheiden. Beispielsweise umfasst BIBFRAME auch Aspekte eines Regelwerks (z. B. Abstraktionsebenen). Man spricht deshalb auch von einem Datenmodell.
* Das waren Metadaten für bibliographische Daten, es gibt auch noch Normdaten und vieles andere z.B. auch administrative Metadaten
    

    
## SLSP - Swiss Library Service Platform
* \> 50 Mitarbeitende
* \> 500 Bibliotheken: https://slsp.ch/bibliotheksnavigator/
* 31 institutionelle Zonen (IZ)
    * und 4 Sandboxes
* Ein gemeinsamer Katalog swisscovery (NZ) Netzwerkzone
    * mit zentralem User-Pool und Anmeldung mit Switch https://eduid.ch/
* Community Zone (CZ) für E-ressourcen weltweit
* **Schätzfrage**: Wie viele Medien?

 ![image](https://hackmd.io/_uploads/B1l1glgvke.png)
* Alma (Bibliothekssytem) und Primo VE (Discovery) von Clarivate (ExLibris) als Cloudlösung
    * Unified Resource Management: E-Ressourcen, physische Bestände, Digitale Objekte
    
### Alma Administration
Aufgeteilt in Funktionsbereiche (Functional Areas), dort Konfiguration und Durchführung von entsprechenden Geschäftsgangen mit Rechte und Rollen ("Warenwirtschaftssystem")
* Erwerbungen umfasst die Bestellung, den Eingang und die Rechnungsstellung für
gedruckte und E-Ressourcen
* **Ressourcen** umfasst Aufgaben rund um die Katalogisierung, Verwaltung physischer
Bestände und die Aktivierung elektronischer Ressourcen
* Discovery umfasst alle Konfigurations- und Anpassungsmöglichkeiten für Primo VE
- Benutzung umfasst die Ausleihe und Vormerkung, d.h. z. B. Arbeitsabläufe, die aufzeigen,
wie Vormerkungen von Benutzenden ausgeführt werden
* Administrator umfasst die Benutzerverwaltung und allgemeine Verwaltungsaufgaben
* Analytics umfasst die statistischen Erhebungen (für dieses Modul ist eine besondere
Mitarbeitendenrolle erforderlich)


### Third Party Systems 

* Was fällt Ihnen als Beispiel ein?

![image](https://hackmd.io/_uploads/SJ_eNlgDye.png)


Alma bietet die Integration mit einer Reihe von Anwendungen von Drittanbietern und wichtigen Unternehmenssystemen, die heute auf dem Campus eingesetzt werden, darunter für Dienste wie Finanz- und Bestellsysteme, Selbstverbuchung, Drucker, Fernleihe, Proxy Services, Inkassodienste und Enterprise Resource Planning (ERP)-Systeme sowie Discovery.
    
    
neben SRU:
* REST API Alma / Primo
* S/FTP
* OAI-PMH
* Electronic Data Interchange (EDI) für Lieferantenkommunikation:  Bestellungen, Reklamationen, Stornierungen, Rechnungen
    
    
Dokumentation:
* ExLibris Knowledge Center: https://knowledge.exlibrisgroup.com/Alma/Product_Materials/050Alma_FAQs/General/Integrations 
* ExLibris Developer Network: https://developers.exlibrisgroup.com/alma/integrations/ 
* Supported Standards: https://developers.exlibrisgroup.com/about/standards/ 


    

## Gruppenübung: Alma Import

### Hintergrund: Datenmodell in Alma

![image](https://hackmd.io/_uploads/Sy6n3-RD-e.png)

Quelle: https://knowledge.exlibrisgroup.com/Alma/Product_Materials/050Alma_FAQs/Metadata_Management/01_General

### Hinweise

* Temporärer Login für [HPH Sandbox](https://slsp-hph-psb.alma.exlibrisgroup.com) (IZ haute école pédagogique):
    * 
    * 
* Vertraut machen mit dem Konzept einer [Sandbox](https://knowledge.exlibrisgroup.com/Alma/Product_Documentation/Alma_Online_Help_(Deutsch)/010Einf%C3%BChrung/040Arbeiten_mit_den_Alma-Sandbox-Umgebungen#Unterschiede_zwischen_der_Alma-Sandbox_und_der_Produktions-Umgebung) 
* Schauen sie sich um finden Sie z.B. MARC21 Bibliographic in der Ressourcenkonfiguration

**Bibliomedia**:

>Bibliomedia unterstützt die öffentlichen Bibliotheken in der Schweiz mit ihrer einzigartigen Ressourcenbibliothek bei der Vermittlung von Sprach- und Lesekompetenz. Unsere zentrale Dienstleistung ist die Ausleihe von bedarfsgerecht zusammengestellten Medienkollektionen.

* tempörer Bestand, der immer wieder importiert und gelöscht werden muss
* Echte Daten: verschiedene files auf Github: https://github.com/Rouven-Schabinger/bain-alma-import

* Collection_S56997.xml (Anbieter) wurde **vorher** zu processed_Collection_S56997.xml umgewandelt mit python
    * Barcode und Callnumber Normalisierung
    * Feldersortierung
    
![image](https://hackmd.io/_uploads/B1FIukgwJx.png)
    -->
![image](https://hackmd.io/_uploads/SyWFu1lPJe.png)

* Normalisierungsregel in Alma (**nachher**) mit drool / XSL

**Aufgabe**:
Importieren einer Datei
    
* Importprofil erstellen
https://knowledge.exlibrisgroup.com/Alma/Product_Documentation/Alma_Online_Help_(Deutsch)/040Ressourcen-Verwaltung/030Datensatz-Import/020Importprofile_verwalten
    * Use Network Zone: NO
    * Profilname: BAIN Bibliomedia Import Gruppe X
    * Normalisierungsregel: SLSP_Bibliomedia-import
    * Inventory Mapping
![image](https://hackmd.io/_uploads/B1e4bM0FJg.png)
![image](https://hackmd.io/_uploads/H1krZfCKJl.png)
![image](https://hackmd.io/_uploads/SykI-MCYJl.png)
    
    
* Importieren
    * Report des Jobs anschauen
    * Records anschauen
### Erkenntnisse? Fragen?






## Fazit

* Wir haben verbreitete Metadatenstandards im Biblioheksvergleich angeschaut und verglichen
* Wir haben das Bibliothekssystem Alma in seiner Konsortium-Realisierung (NZ,IZs) und in der Schweiz kennengelernt.
    * Administration
    * Third Party Systems
* Wir haben MARC-Dateien in eine IZ-Sandbox von Alma importiert


## Lehrevaluation: Schwammigster Punkt
* Was war heute für mich am unklarsten, verwirrendsten oder der offenste Punkt? (mündlich)