---
title: BAIN FS25 - Funktion und Aufbau von Bibliothekssystemen

---

# BAIN FS25 - Funktion und Aufbau von Bibliothekssystemen



# Agenda

* Lerntagebücher
* Metadatenstandards in Bibliotheken (MARC21)
* Konfiguration von Koha

## Lerntagebücher




## Metadatenstandards in Bibliotheken (MARC21)




* TODO: Unterschied zwischen Datenformat und Datenmodell in der Bibliotheks-IT (auch in Bezug auf Regelwerke bzw. inhaltliche Vorgaben)
* 
Datenmodell, mehr als format, inkludiert regelwerk?
Regelwerk eher inhaltich, weniger technisch

* MARC21: International verbreiteter Metadaten-Standard, begründet von der Library of Congress 1999: <https://www.loc.gov/marc/bibliographic/>
* Hat [eigenes Binärformat](http://format.gbv.de/marc/iso) (.mrc), gibt's aber auch [als XML](http://format.gbv.de/marc/xml)
* wegen unterschiedlicher Katalogisierungsregeln und der Möglichkeit eigene Felder zu belegen, weicht die Verwendung international und auch nach Institution [stark vom vermeintlichen Standard ab](https://docs.google.com/presentation/d/e/2PACX-1vRU4J_rln00UVD7pNPT0_02NOad0HfSk_UKqRI0v29y8QkMAplEDlyjc0Ot_VE_paV6WBW29Fh_V-iN/pub?start=false&loop=false&delayms=3000#slide=id.g574306292a_0_35)
* Koha und alle anderen großen Bibliothekssysteme basieren auf MARC21 oder unterstützen es als Austauschformat
* wird zukünftig voraussichtlich von [BIBFRAME](http://format.gbv.de/bibframe), einem Datenmodell basierend auf [RDF](http://format.gbv.de/rdf), abgelöst

### Übung: Vergleich MARC21 und Dublin Core

* Dublin Core ist ein Standard, der als kleinster gemeinsamer Nenner gilt
    * geht über die Bibliothekswelt hinaus
* Wir beziehen die Daten über die SRU-Schnittstelle von Swisscovery (auf das Thema Schnittstellen und SRU gehen wir an einem anderen Tag noch ein)

**Aufgabe (15 Minuten):** Laden Sie über die folgenden Links Daten über die SRU-Schnittstelle von Swisscovery einmal im Format MARC21 und einmal im Format Dublin Core und vergleichen Sie diese.

* MARC21: https://swisscovery.slsp.ch/view/sru/41SLSP_NETWORK?version=1.2&operation=searchRetrieve&query=title=einstein&recordSchema=marcxml
* Dublin Core: https://swisscovery.slsp.ch/view/sru/41SLSP_NETWORK?version=1.2&operation=searchRetrieve&query=title=einstein&recordSchema=dc

**Hintergrundinfos zu swisscovery:**

- Der Katalog Swisscovery beinhaltet die Daten der an SLSP teilnehmenden Bibliotheken.
- Der gemeinsame Katalog ermöglicht eine übergreifende Suche, gleichzeitig bietet Swisscovery auch Schnittstellen an, über welche Metadaten der teilnehmenden Institutionen zentral bezogen werden können.
- Siehe auch: [Nutzung SLSP-Metadaten](https://slsp.ch/de/metadata), [Dokumentation der SRU-Schnittstelle von ALMA](https://developers.exlibrisgroup.com/alma/integrations/sru/)

### Erkenntnisse? Fragen?

* DC besser menschlesbar ohne Dokumentation z.b.:
    * <<dc:title>>... und Einstein hatte doch recht</dc:title>  VS
    * <datafield ind1="1" ind2="0" tag="245"> ; <subfield code="a">... und Einstein hatte doch recht</subfield>
* DC braucht weniger platz für ein Dokument
* Ist MARC besser maschinelesbar als DC? Es sieht so aus.
    * -->maschinenlesbar sind beide, MARC21 ist spezifischer und besser verwertbar
* Welche Datenmodell nutzt SLSP/Alma für seine Metadaten? DC, MARC oder beide?
* kein Feld für Übersetzer bei DC? Bei MARC21 Autor und Übersetzer im gleichen Subfield von Titelfeld 245
    * -->Übersetzer könnte man bei MARC21 auch in den 700er Feldern erfassen, diese Felder dürfen auch mehrfach verwendet werden

* Reihenfolge ist bei beiden nicht gleich. --Vergleiche "<description>" bzw "<subfield>" von beiden Formaten

* Bei Dublin Core fehlen wichtige bibliographische Metadaten wie: 
    - Erscheinungsort
    - Verlag   -->gäbe ein Feld Publisher
    - Umfang (Seitenzahlen)
    - Angaben zur Auflage 
    
--> kann auch in Feld Description kopiert werden oder wird weggelassen --> Informationsverlust
--> Erkenntnis: DC nicht so gut wie es sein könnte
* Ich bin nicht sicher, was genau wir ansehen, andere Titel gefunden:
  - Und sie segelten weiter (Buch)
  - Du musst mir helfen, sonst werde ich verrückt (Artikel)

  Es wäre interessant zu wissen, wonach gesucht wird.
### Regelwerk vs. Datenformat

* Ein Regelwerk bildet die *theoretische* Grundlage für die Katalogisierung. Es definiert, wie eine Ressource zu beschreiben ist. Dazu gehören in der Regel inhaltliche Kategorien und normierte Vokabulare.
    * Functional Requirements for Bibliographic Records (FRBR) und Resource Description and Access (RDA) sind Regelwerke
* Ein Datenformat erlaubt die *praktische* Repräsentation eines Katalogisats. Es definiert, wie Informationen zu kodieren sind. Dazu gehören Datenstrukturen und -typen.
    * MARC21 und BIBFRAME sind Datenformate

Note:
* Regelwerke und Datenformate ergänzen einander und sind nicht immer trennscharf zu unterscheiden. Beispielsweise umfasst BIBFRAME auch Aspekte eines Regelwerks (z. B. Abstraktionsebenen). Man spricht deshalb auch von einem Datenmodell.
    

    
## SLSP - Swiss Library Service Platform
* \> 50 Mitarbeitende
* \> 500 Bibliotheken: https://slsp.ch/bibliotheksnavigator/
* 31 institutionelle Zonen (IZ)
* Ein gemeinsamer Katalog swisscovery (NZ) Netzwerkzone

 ![image](https://hackmd.io/_uploads/B1l1glgvke.png)
* Alma (Bibliothekssytem) und Primo VE (Discovery) von Clarivate
    
### Alma Administration
* Metadata Konfiguration

### Third Party Systems 
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

    
### Migrationen
z.B.: https://github.com/Rouven-Schabinger/bain-alma-import/blob/main/000000080_LLB01000502511.xml
    

## Gruppenübung: Bibliomedia Import
>Bibliomedia unterstützt die öffentlichen Bibliotheken in der Schweiz mit ihrer einzigartigen Ressourcenbibliothek bei der Vermittlung von Sprach- und Lesekompetenz. Unsere zentrale Dienstleistung ist die Ausleihe von bedarfsgerecht zusammengestellten Medienkollektionen.
* verschiedene files auf Github: https://github.com/Rouven-Schabinger/bain-alma-import
* Temporärer Login für HPH Sandbox (IZ haute école pédagogique):
    * user
    * pw
* Collection_S56997.xml (Anbieter) wird zu processed_Collection_S56997.xml  
    * Barcode und Callnumber Normalisierung
    * Feldersortierung
    
![image](https://hackmd.io/_uploads/B1FIukgwJx.png)
    -->
![image](https://hackmd.io/_uploads/SyWFu1lPJe.png)
    
* Importprofil erstellen
* Normalisierungsregel
    
## Aufgabe bis 5. März

* Lerntagebuch einrichten (vgl. Lehreinheiten 01 und 02)
* Neu: Eintrag im Lerntagebuch zu dieser Lehreinheit
    
    


### Einführung in Koha

* Webseite: <https://koha-community.org>
* Weltweites Open Source Projekt, gegründet 1999 in Neuseeland, heute  mit Beteiligung von Unternehmen wie ByWater Solutions, Biblibre,  Catalyst IT, PTFS Europe, Theke Solutions
* Status des Projekts: Siehe [Statistik bei Open Hub](https://www.openhub.net/p/koha)

Note:
- Zur Gesundheit von Open-Source-Projekten siehe auch https://felixlohmeier.de/slides/2017-09-28_vufind-anwendertreffen-keynote.html
- Zur Bedeutung von Open-Source-Software auch dieser Comic: https://xkcd.com/2347/

#### Koha Dokumentation

* Professionelle Entwicklungsstrukturen, vgl. Dashboard: <https://dashboard.koha-community.org>
* Release Notes zur Version 23.11: <https://koha-community.org/koha-23-11-released/>
* Handbuch zur Version 23.11: [englisch](https://koha-community.org/manual/23.11/en/html/), [deutsch](http://koha-community.org/manual/23.11/de/html/index.html) (Übersetzung noch in Arbeit)

#### Koha Demo

* MARC21, Koha 23.11 bereitgestellt von schweizer Unternehmen "Admin Kuhn"
  * Dienstoberfläche: https://koha.adminkuhn.ch:8443
  * OPAC: https://koha.adminkuhn.ch:443
* Login mit Benutzername `demo` / Passwort `demo` möglich
* wird jeweils Morgens um 5 Uhr auf Standardwerte zurückgesetzt
* siehe auch die Erläuterungen unter http://adminkuhn.ch/wiki/Koha-Demoinstallation

### Grundkonfiguration mit Tutorial

Die Grundkonfiguration in der Demo-Installation von Koha ist bereits erledigt. Daher schauen wir uns gemeinsam ein Tutorial an, um die Einstellungen kennenzulernen.

Wir verwenden dazu ein Tutorial von Stephan Tetzel, das auf deutsch und englisch verfügbar ist:

* Deutsch: <https://zefanjas.de/wie-man-koha-installiert-und-fuer-schulen-einrichtet-teil-1/> 
* Englisch: <https://openschoolsolutions.org/how-to-install-and-set-up-koha-for-schools-part-1/> 

Note:
- Da wir eine neuere Koha-Version (23.11) als im Tutorial 20.05 verwenden, gibt es Abweichungen im Detail. Das ist eine Situation, die in der Praxis oft auftritt. Versuchen Sie die Hinweise im Tutorial sinngemäß anzuwenden.

    
## Übung: Manuelle Bedienung

**Aufgabe (20 Minuten)**: Damit Sie ein Gespür für das System erhalten, machen wir nun ein Minimalbeispiel für einen vereinfachten Bibliotheksworkflow:

1. Buch erfassen
2. Benutzer anlegen
3. Buch an Theke ausleihen
4. Buch an Theke zurücknehmen

Schauen Sie sich dabei auch ein wenig um, welche Optionen das Bibliothekssystem Koha bietet.

### Buch erfassen

Start > Katalogisierung > Neuer Titel > Schnellaufnahme

1. Neuer Marc Datensatz: Pflichtfelder ausfüllen
    * `000` und `008` werden automatisch befüllt beim Anklicken
    * In `245a` muss ein Titel vergeben werden
2. Exemplar hinzufügen
    * `p - Barcode` muss vergeben werden (sonst können wir später nicht ausleihen)
    * Unten Button "Exemplar hinzufügen" nicht vergessen

### Benutzer anlegen

* Start > Benutzer > Benutzer-Schnellerfassung
* Hinzufügen Benutzer: Name und Ausweisnummer vergeben

### Buch an Theke ausleihen

**Hier gibt es leider einen Fehler in der Demo-Installation: Beim Versuch eine Ausleihe zu tätigen erscheint eine Fehlermeldung (Error 500)**

* Oben im Suchschlitz Reiter Ausleihe wählen, Ausweisnummer eingeben und abschicken
* Dann in Box "Ausleihe an" den Exemplarbarcode eingeben und Ausleihe abschicken
* Über Button "Zeige Ausleihen" prüfen, ob Ausleihe erfolgreich war

### Buch an Theke zurücknehmen

* Oben im Suchschlitz Reiter Rückgabe wählen, Barcode eingeben und abschicken

### Fragen? Erkenntnisse?
    
* Intuitive Nutzung (obwohl ich nicht in einer Bibliothek arbeite)
* die viele feldern bei marc21 macht die übung schwieriger. welche sind relevant? einige, die pflicht sind, verstehe ich nichz und habe keine ahnung was zuhinzufügen.
* Bei Werkzeuge -> Kalender können Schliesstage definiert werden.
* Ich frage mich, wie viel Zeit es dauern würde, jedes Medium in den Katalog aufzunehmen. Kann man Daten von anderen Stellen übernehmen, kann man sie exportieren? Was die Benutzer angeht, finde ich es toll, aber reicht es aus, Name und ID hinzuzufügen? Was ist mit der Adresse z.B.? (--bei Jugendliche anders)