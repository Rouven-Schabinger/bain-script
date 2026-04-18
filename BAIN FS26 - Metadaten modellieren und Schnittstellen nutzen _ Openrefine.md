# BAIN FS25 - Metadaten modellieren und Schnittstellen nutzen | Openrefine




## OpenRefine

[![](https://openrefine.org/img/openrefine_logo.svg)](https://openrefine.org/)

### Einführung in OpenRefine

* Claim
* Einsatzbereiche
* Anwender\*innen
* Formate
* Einsatzmöglichkeiten
* Historie

#### Claim von OpenRefine

>  "A free, open source, powerful tool for working with messy data"

* grafische Oberfläche, die einer klassischen Tabellenverarbeitungssoftware ähnelt
* dient der Analyse, Bereinigung, Konvertierung und Anreicherung von Daten
* wird in der Regel lokal auf einem Computer installiert und über den Browser bedient

#### Nutzerumfrage 2024

https://openrefine.org/blog/2024/12/20/2024-survey-results

#### Von OpenRefine unterstützte Formate

* Besonders geeignet für tabellarische Daten (CSV, TSV, XLS, XLSX und auch TXT mit Trennzeichen oder festen Spaltenbreiten)
* Einfaches "flaches" XML (z.B. MARCXML) oder JSON ist mit etwas Übung noch relativ einfach zu modellieren
* Komplexes XML mit Hierarchien (z.B. EAD) ist möglich, aber nur mit Zusatztools
* Kann auch [in Kombination mit MarcEdit](https://blog.reeset.net/archives/1873) für Analyse und Transformation von MARC21 benutzt werden

#### Einsatzmöglichkeiten von OpenRefine

* Exploration von Datenlieferungen
* Vereinheitlichung und Bereinigung (zur Datenqualität in der Praxis siehe Präsentation von Peter Király ["Validating 126 million MARC records"](https://docs.google.com/presentation/d/e/2PACX-1vRU4J_rln00UVD7pNPT0_02NOad0HfSk_UKqRI0v29y8QkMAplEDlyjc0Ot_VE_paV6WBW29Fh_V-iN/pub))
* Abgleich mit Normdaten ("Reconciliation") in Wikidata, GND und VIAF
* Für lokalen Einsatz ausgelegt (Installation auf Webservern und Automatisierung möglich, aber nur mit Zusatzsoftware)
* [AI Extension for OpenRefine](https://github.com/sunilnatraj/llm-extension/releases/ )

#### Historie

<https://github.com/OpenRefine/OpenRefine/graphs/contributors>

Note:
- 2010-05: Freebase Gridworks
- 2011-12-11: Google Refine 2.5
- 2015-04-30: OpenRefine 2.6 rc1
- ...

### Installation OpenRefine

https://github.com/Rouven-Schabinger/bain-openrefine

siehe ReadMe

### Grundfunktionen

* Wir gehen nun ein paar Basisfunktionen gemeinsam durch, damit Sie einen Eindruck von der Software erhalten.
* Später im Kurs werden wir OpenRefine nutzen, um weitere Daten in MARCXML zu konvertieren.

#### Beispieldaten laden

* Create Project > Web Addresses (URL)
  * https://raw.githubusercontent.com/LibraryCarpentry/lc-open-refine/gh-pages/data/doaj-article-sample.csv
* Automatisch erkannte Einstellungen für den Import können so belassen werden.
* Mit Button `Create Project` oben rechts den Import starten.

#### Vorführung von Basisfunktionen

1. Spalte Language > Facet > Text Facet
2. Spalte Authors > Edit cells > Split multi-valued cells... > Separator: |
3. Spalte Authors > Edit cells > Cluster and edit...
4. Spalte Authors > Edit cells > Join multi-valued cells... > Separator: |

#### Vorführung von Basisfunktionen

1. Spalte Licence > Facet > Text facet
    * Was ist die am häufigsten vergebene Lizenz
    * Wieviele Artikel haben keine Lizenz?
2. Spalte Publisher > Facet > Text facet
    * Warum erscheint MDPI AG zweimal?
    * Wie lässt sich das korrigieren?

### Übung
* Lesen und bearbeiten Sie die Lektionen welche die Inhalte widergeben, welche ich oben gezeigt habe  [Lehrmaterialien von Library Carpentry zu OpenRefine](https://librarycarpentry.org/lc-open-refine/)
* Optional, schauen Sie sich die anderen Inhalte an


#### Fragen / Ergebnisse

### Erweiterte Funktionen

#### Vorführung Reconciliation

* Ziel: Über die ISSN Informationen zur Zeitschrift ergänzen
* Spalte Citation > Edit column > Add column based on this column...
  * Name: Journal
  * Expression: `value.split(",")[0]`
* Spalte Journal > Reconcile > Start reconciling
  * Wikidata reconci.link (en) auswählen
  * links "Reconcile against no particular type" auswählen
  * rechts "ISSNs" aktivieren und in Textfeld ISSN eingeben und P236 anklicken
* Spalte Journal > Edit column > Add columns from reconciled values...
  * official website (P856)
  * configure: Limit auf 1 setzen



### Beispiel für weitere Datenquelle: lobid-gnd

* Webseite: [lobid-gnd](https://lobid.org/gnd)

* Folien: [Abgleich & Anreicherung eigener Daten mit der GND](https://slides.lobid.org/2021-kim-reconcile/2021-kim-reconcile.pdf)

* Adresse für Eintrag in OpenRefine: https://lobid.org/gnd/reconcile/

Beispieldaten Schriftsteller\*innen:

```
Name,Geburtsdatum
Ernst Jünger,29.03.1895
Hilde Domin,27. Juli 1909
Hermann Hesse,2.7.1877
Gertrud von LeFort,11.10.1876
Johann Wolfgang von Goethe,1749
Sarah Kirsch,1935
Friedrich von Schiller,10. November 1759
Ricarda Huch,18.7.1864
Karl Wolfskehl,1869
Luise Rinser,30. April 1911
```

* Kürzen auf 4 stelliges Jahr mit find: https://openrefine.org/docs/manual/grelfunctions#basic-string-modification
und RegEx, Bsp.
```
Hello123
World456
Test789

value.find(/[A-Za-z]+/)[0]

"Hello123" → "Hello"
"World456" → "World"
"Test789" → "Test"
```

* Test des RegEx /[A-Za-z]+/ via https://regex101.com/
* Cheat-Sheet: https://www.rexegg.com/regex-quickstart.php
### Übung
 1. Datensatz (articles): Fügen Sie auch für Journals via ISSN eine Reconciliation (Wikidata) durch und ergänzen sie z.B. das Erscheinungsland
 2. Datenstatz (autoren): transformieren Sie das Gebertsjahr und führen Sie dann eine Reconciliation (lobid)  durch und ergänzen sie z.B. das Geburtsland


#### Fragen / Ergebnisse

### CSV nach MARCXML mit OpenRefine

* Wir nutzen die Funktion [Templating Exporter](https://docs.openrefine.org/manual/exporting#templating-exporter). Diese findet sich oben rechts im Menü Export > Templating
* Beschreibung des MARC21 Formats für bibliografische Daten mit Liste der Felder: <https://www.loc.gov/marc/bibliographic/>
* Beispieldatei der Library of Congress für MARC21 mit mehreren Dokumenten: <https://www.loc.gov/standards/marcxml/xml/collection.xml>

Note:
- Das Vorgehen ist ähnlich wie bei XSLT Crosswalks, nur dass das "Template" hier direkt bearbeitet werden kann und nicht bereits fest steht, wie bei MarcEdit.
- OpenRefine verwendet eine eigene Template-Sprache (GREL) statt XSLT.

#### Voraussetzung für die Übung

* OpenRefine (lokal oder auf dem Server)
* Ein Projekt mit den Beispieldaten aus der Library Carpentry Lesson.
* Schnell neu zu erstellen mit: Create Project > Web Addresses (URL)
  * https://raw.githubusercontent.com/LibraryCarpentry/lc-open-refine/gh-pages/data/doaj-article-sample.csv

#### Vorlage als Ausgangsbasis

* Prefix:
    ```xml
    <collection xmlns="http://www.loc.gov/MARC21/slim">
    ```
* Row Separator: (Zeilenumbruch)
* Suffix:
    ```xml
    </collection>
    ```

* Row Template:

    ```xml
    <record>
    <leader>     nab a22     uu 4500</leader>
    <controlfield tag="001">{{cells['URL'].value.replace('https://doaj.org/article/','').escape('xml')}}</controlfield>
    <datafield tag="022" ind1=" " ind2=" ">
        <subfield code="a">{{cells['ISSNs'].value.escape('xml')}}</subfield>
    </datafield>
    <datafield tag="100" ind1="0" ind2=" ">
        <subfield code="a">{{cells['Authors'].value.split('|')[0].escape('xml')}}</subfield>
    </datafield>
    <datafield tag="245" ind1="0" ind2="0">
        <subfield code="a">{{cells["Title"].value.escape('xml')}}</subfield>
    </datafield>{{
    forEach(cells['Authors'].value.split('|').slice(1), v ,'
    <datafield tag="700" ind1="0" ind2=" ">
        <subfield code="a">' + v.escape('xml') + '</subfield>
    </datafield>')
    }}
    </record>
    ```

#### Aufgabe 1: "Reverse Engineering"

* Beschreiben Sie anhand des Vergleichs der Ausgangsdaten mit dem Ergebnis mit ihren eigenen Worten welche Transformationen für die jeweiligen Felder durchgeführt wurden.
* Versuchen Sie die Aufgabe in der Gruppenarbeit zunächst einzeln zu lösen  und diskutieren Sie dann in der Gruppe.
* Dokumentieren Sie abschliessend bitte hier das Gruppenergebnis.

#### Fragen / Ergebnisse




#### Aufgabe 2: Template ergänzen

* Suchen Sie für weitere Spalten in den DOAJ-Daten die Entsprechung in MARC21: <https://www.loc.gov/marc/bibliographic/>
* Erstellen Sie geeignete Regeln im Template, um die Daten der gewählten Spalten in MARC21 zu transformieren.
* Dokumentieren Sie das gewählte MARC21-Feld und den zugehörigen Abschnitt aus dem Template.
* Wenn die Spalten leere Zellen enthalten, dann Funktion `forNonBlank()` nutzen. Beispiel:

```xml
{{
forNonBlank(
    cells['DOI'].value,
    v,
    '<datafield tag="024" ind1="7" ind2=" ">
        <subfield code="a">' + v.escape('xml') + '</subfield>
        <subfield code="2">doi</subfield>
    </datafield>',
    ''
)
}}
```

#### Fragen / Ergebnisse


#### Aufgabe 3: XML gegen XSD-Schema validieren

* Wir exportieren das Gesamtergebnis als XML-Datei.
  * Tipp: Firefox speichert Datei im Downloads-Ordner als .txt. Ordner Downloads aufrufen und Ende umbenennen in .xml
* Für die Validierung können Sie den Webservice https://www.softwarebytes.org/xmlvalidation/ (Registrierung) oder https://www.freeformatter.com/xml-validator-xsd.html nutzen.
* Das offizielle XSD-Schema der Library of Congress ist unter folgender Adresse erreichbar: https://www.loc.gov/standards/marcxml/schema/MARC21slim.xsd

#### (Optional) Aufgabe 4: Einsatzszenarien

* Überlegen Sie Einsatzszenarien von OpenRefine in Ihrer Einreichtung / Ihrer Berufspraxis und Skizzieren Sie einen workflow (Schritte wie sie in der OpenRefine History auftauchen würden)
oder
* Suchen Sie online nach OpenRefine-Realisierungen im Bibliotheks- oder Archivbereich

#### Fragen / Ergebnisse

...

### Literatur

* Weitere Optionen für den Export in MARCXML finden Sie im OpenRefine Wiki: https://github.com/OpenRefine/OpenRefine/wiki/Export-as-MARCXML

*  Data Cleaning in OpenRefine (Library Skills Week 2021): https://www.youtube.com/watch?v=RhaDVmLT-Ck

