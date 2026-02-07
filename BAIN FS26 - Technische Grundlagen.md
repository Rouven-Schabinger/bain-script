# BAIN FS26 - Technische Grundlagen

## Agenda

Heute: Technische Grundlagen und Kennenlernen

Ablauf:
* Lehrinhalte
* Organisatorisches
* Vorstellungsrunde
* Einrichtung der Arbeitsumgebung

## Vorstellungsrunde I

Rouven Schabinger  ([ORCID](https://orcid.org/0000-0002-0249-7917), [LinkedIn](https://www.linkedin.com/in/rouven-schabinger-7ba1a833b/))
* Erste Durchführung Bibliotheks- und Archivinformatik 2025
* Studium Bibliotheks- und Datenmanagement
* Arbeitserfahrung in wissenschaftlichen Bibliotheken 
(Württembergische Landesbibliothek Stuttgart, KIT Bibliothek) 2014-2023
* Swiss Library Service Platform (SLSP) 2023-
  * System Betrieb- und Weiterentwicklung
  * Migrationen
  * Integration von Drittsystemen, Schnittstellen
  

## Organisatorisches
* Zentraler Einstieg über den Moodle-Kurs


    * [Moodle (ZH)](https://moodle.fhgr.ch/course/view.php?id=22668)
    * [Moodle (CHR)](https://moodle.fhgr.ch/course/view.php?id=22667)

Dort:
* Modulbeschreibung 
* Semesterinformation
* Ankündigen: Falls sich etwas an einer Veranstaltung ändern sollte
* Diskussionforum: Für alle Fragen die sich während den Veranstaltungen ergeben. Auch gern für untereinander antworten.

### Zeitumfang und Abgabetermin

* Gemäss Kurshandbuch sind 80 Stunden für Selbststudium (für Übungen und Lerntagebuch) vorgesehen.
* Abgabetermin für Lerntagebücher

### Lehrmaterialien

* Für Notizen und zum Austausch verwenden wir Dokumente in [HackMD](https://hackmd.io/). Alle, die den Link kennen, können es bearbeiten. Zur Formatierung wird [Markdown](https://www.markdownguide.org/basic-syntax/) verwendet.
* Kurs basiert auf Inhalten von Rudolf Mumenthaler (Direktor der Universitätsbibliothek Zürich) und Felix Lohmeier (IT-Berater).



## Vorstellungsrunde II


Fragen (ohne Namen):

**1. Was verstehen Sie unter Bibliotheks- und Archivinformatik (BAIN)?
Was gehört Ihrer Meinung nach nicht zu BAIN?**

**2. Motivation / Erwartungshaltung: Was erwarten Sie persönlich von diesem Kurs? Fehlen Inhalte?**

**3. Praxiserfahrungen: Hatten Sie bereits ausserhalb der Hochschule mit Bibliotheks- oder Archivsoftware zu tun? Welche?**

**4. Einschätzung IT-Grundlagen (UNIX Shell, Git, Python/Pandas, Metadaten ...)?**

## Einrichtung der Arbeitsumgebung

* Wer hat ein Konto bei GitHub?
* Wer hat bereits GitHub Codespaces genutzt?

### Registrierung bei GitHub

* Was ist GitHub, was ist Git?
https://librarycarpentry.github.io/lc-git/01-what-is-git.html

https://www.github.com -> Sign Up

#### Angemeldet?

Bitte hier eintragen, wenn Sie sich erfolgreich registriert und angemeldet haben. Pseudonym geht auch.

**Username**:

### Codespace starten

* Repository aufrufen: https://github.com/Rouven-Schabinger/bain-lc-unix-shell
* Button `Code` / Tab `Codespaces` / Button `Create codespace on main`

![Screenshot 2025-01-05 105724](https://hackmd.io/_uploads/BkY2D0wU1e.png)



### Codespace beenden

1. https://github.com/codespaces aufrufen
2. vorhandene Codespaces beenden oder gleich löschen



## Timeout in Codespaces erhöhen 

### Einstellungen aufrufen

1. über Profilfoto oben rechts und dort `Settings` aufrufen
2. Links Rubrik `Codespaces` auswählen

![](https://pad.gwdg.de/uploads/93466426-b238-4abe-99aa-35eb70a6a02b.png)

### Timeout auf `240 Minuten` erhöhen

![](https://pad.gwdg.de/uploads/7426fdc7-f278-4630-83df-cba152585a73.png)

## Grundlagen der Unix Shell

* Wird benötigt zur Administration von Servern
* Ist aber auch zur Automatisierung von kleineren Aufgaben beliebt (Shell-Scripte)


### Übung: Dateisystem

Bearbeiten Sie in aller Ruhe die Kapitel 2 (Navigating the filesystem) und 3 (Working with files and directories) der [Library Carpentry Lesson zur Unix Shell](https://librarycarpentry.org/lc-shell/02-navigating-the-filesystem.html) im vorhin gestarteten Codespace
  1. Webseite zur Lesson aufrufen.
  2. Dort genannte Befehle in das Terminal im Codespace eingeben und nachvollziehen.

Hinweis: Die Lesson geht von einem typischen Desktop-Linux aus, daher die Verzeichnisse Desktop Music etc. Im Codespace weichen die Verzeichnisse davon ab. Die Übungsmaterialien für Kapitel 3 sind abweichend von der Angabe in der Lesson also nicht unter `Desktop/shell-lesson`, sondern direkt unter `shell-lesson` zu finden. Das ist ein indirekter Test, ob Sie sich gut in der Shell zurechtfinden :-).

[![](https://pad.gwdg.de/uploads/67ec46f5-df9c-489b-86e3-40150b21ff1b.jpg)](https://librarycarpentry.org/lc-shell/02-navigating-the-filesystem.html)




### Tipps zur Unix Shell

* Copy & Paste im Terminal: Bei Problem Shift+Einfg oder warten bei Mauseinfügen
* Vorsicht im Browser mit `STRG`+`W` (das kann Tab schliessen). Was macht es im Terminal?
* Nutzen Sie immer die Tab-Taste für die Autovervollständigung
* Seien Sie faul, verwenden Sie Ihre persönliche Befehlshistorie (Pfeiltaste nach oben / Suche in der Historie mit `STRG`+`R`)
* Nutzen Sie Spickzettel für die wichtigsten Kommandos wie z.B.
  * [Library Carpentry Reference](https://librarycarpentry.org/lc-shell/reference.html)
  * [Cheatsheet für Linux](https://devhints.io/linux)
  * [Cheatsheet für Shell-Scripte](https://devhints.io/bash)

### Übung: Textanalyse mit der Shell (optional)

* [Kapitel 5 Counting and mining with the shell](https://librarycarpentry.org/lc-shell/05-counting-mining.html)
* Exkurs zu Regular Expressions: https://regex101.com
  * Auch dazu gibt es übrigens eine Library Carpentry Lesson  https://librarycarpentry.org/lc-data-intro/01-regular-expressions.html

## Versionskontrolle mit Git

Durch die Plattform GitHub, auf der Informatiker\*innen Ihren Quellcode ablegen, ist das Versionskontrollsystem Git sehr populär geworden. Es ist nicht nur für die Entwicklung von Software, sondern generell für die Zusammenarbeit in Projekten hilfreich.

Wozu Git?
* Git ist eine Software zur Versionskontrolle
* Ermöglicht die Arbeit an Textdateien auf mehreren Computern und/oder mit mehreren Personen zu synchronisieren.
* Jede Änderung wird nachvollziehbar.
* Funktioniert mit allen Textdateien, also geeignet für Code, Plain Text oder auch Tabellen (CSV).

Git wurde entwickelt für die gemeinsame Software-Entwicklung; heute gibt es weitere Anwendungsfälle (z.B. Texte, Präsentationen oder Forschungsdaten).

Unterschiede zwischen Git und GitHub
* Git kann zunächst auch lokal auf einem Computer verwendet werden.
* Wenn ein Git Repository im Netz bereitgestellt werden soll, braucht es eine Installation von Git auf einem Webserver.
* Das kann man selber machen oder eine Plattform nutzen. Die bekannteste ist [GitHub](https://www.github.com).

Viele Bibliotheken und Archive (z.B. [Bundesarchiv](https://github.com/SwissFederalArchives)) nutzen GitHub oder GitLab. 

Es gibt eine gemeinschaftlich gepflegte Liste [BibsOnGitHub](https://github.com/axel-klinger/BibsOnGitHub) seit [10 Jahren](https://www.vbib.net/vbib25-programm/programmdetail/vbib25-corner-6-2), auf der [Listen von Bibliotheken](https://axel-klinger.github.io/BibsOnGitHub/libraries.html) und [deren Repositorien](https://axel-klinger.github.io/BibsOnGitHub/repositories.html) eingesehen werden können.

### Demo: Typischer Git Workflow

1. Fork erstellen
2. Änderung vornehmen und committen
3. Pull Request anlegen


## Codespace manuell löschen

![](https://pad.gwdg.de/uploads/ae0b611d-4603-474e-822f-9bbced848642.png)


## Fazit

* Wir haben das Organisatorische geklärt: Termine, Leistungsnachweis, etc.
* Ihre Erfahrungen und Erwartungen aus der Vorstellungsrunde werde ich versuchen bei den weiteren Lehrinhalten zu berücksichtigen.
* Sie haben jetzt ein GitHub-Konto und können GitHub Codespaces starten.
* Sie haben die Bedienung des Terminals (Unix Shell) in einer kleinen Übung wiederholt.
* Mit den Library Carpentry Lessons haben Sie Quellen zur Vertiefung im Selbststudium.
* Sie haben kurz gesehen, wie die Versionskontrolle mit Git funktioniert.
* In den folgenden Lehrveranstaltungen geht es weiter mit Funktion und Aufbau von Bibliothekssystemen.

## Lehrevaluation: Schwammigster Punkt
* Was war heute für mich am unklarsten, verwirrendsten oder offensten Punkt? (mündlich)

Punkte:
*  

## Weiterführendes
* Umfrage zum Werdegang und Fähigkeiten von Systembibliothekaren: 

https://igelu.org/wp-content/uploads/2024/10/1662-107997-Mermaid-Whispers-and-System-Insights.pdf

* FHGR Bibliothek: Wie funktioniert diese Maschine?

![image](https://hackmd.io/_uploads/rJPVrqEDZe.png)

* "Lernen Sie aus Ihren Fehlern, und machen Sie dann neue."

## Aufgabe: Lerntagebuch

Bis zum nächsten Termin:

1. Lerntagebuch anlegen
2. Einführungsartikel ("wo bin ich gestartet?")
3. Beiträge zu dieser Lehreinheit "Technische Grundlagen"

Wegen der kurzen Bearbeitungszeit gerne erstmal nur ein paar Stichpunkte.


