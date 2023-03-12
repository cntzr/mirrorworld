---
title: Neovim
date: 2021-03-19
lastmod: 2021-03-19
tags: [ "editor" ]
draft: false
---

## Suchen & Ersetzen

* ```:%s/Suchbegriff/Ersetzung/``` ... ersetzt das erste Vorkommen
* ```:%s/Suchbegriff/Ersetzung/g``` ... ersetzt alle Vorkommen
* ```:%s/Suchbegriff/Ersetzung/gi``` ... ersetzt alle Vorkommen unabhängig von Groß-/Kleinschreibung

## Rechtschreibung

* ```CTRL + x und dann s``` ... liefert im Eingabemodus Korrekturvorschläge für ein falsch geschriebenes Wort
* ```[s``` ... springt zum vorherigen Schreibfehler
* ```]s``` ... springt zum nächsten Schreibfehler
* ```zg``` ... fügt ein unbekanntes Wort zum Wörterbuch hinzu
* ```z=``` ... liefert Korrekturvorschläge analog oben

## Navigation

* ```h | j | k | l``` ... Cursor nach links, unten, oben oder rechts
* ```w``` ... springt zum Anfang des nächsten Wortes
* ```b``` ... springt zum Anfang des vorherigen Wortes
* ```e``` ... springt zum Ende des nächsten Wortes
* ```f*``` ... setzt den Cursor auf das erste Vorkommen von * oder was auch immer
* ```CTRL + y``` scrollt Fensterinhalt um eine Zeile nach oben
* ```CTRL + e``` scrollt Fensterinhalt um eine Zeile nach unten
* ```CTRL + u``` bewegt Fensterinhalt und Cursor um einen halben Bildschirm nach oben
* ```CTRL + d``` bewegt Fensterinhalt und Cursor um einen halben Bildschirm nach unten
* ```zt``` fixiert Cursor und bewegt Fensterinhalt so, dass der Cursor in der ersten Zeile steht
* ```zz | z.``` fixiert den Cursor und bewegt Fensterinhalt so, dass der Cursor in der Bildschirmmitte steht
* ```zb``` fixiert Cursor und bewegt Fensterinhalt so, dass der Cursor in der letzten Zeile steht
* ``H``` fixiert den Bildschirm und setzt den Cursor in die erste Zeile
* ``M``` fixiert den Bildschirm und setzt den Cursor in die Bildschirmmitte
* ``L``` fixiert den Bildschirm und setzt den Cursor in die letzte Zeile

## NerdCommenter

* ```,cc``` ... kommentiert aktuelle Zeile
* ```,cs``` ... optisch ansprechender Kommentar des visuell selektierten Textblocks
* ```,cm``` ... kommentiert visuell selektierte Zeilen mit minimalem Aufwand
* ```,cu``` ... unkommentiert visuell selektierte Zeilen

## vim-go

* ```:GoInstallBinaries``` installiert die Go Tools (c;
* ```:GoUpdateBinaries``` aktualisiert die Go Tools, insbesondere für den _delve_ Debugger interessant
* als Leader ist "," eingestellt
* ```:GoRun | ,r``` führt _go run_ aus
* ```:GoTest | ,t`` führt _go test_ aus
* ```:GoTestFunc``` testet nur die Function unter dem Cursor
* ```:GoTestCompile``` testet und compiliert
* ```:GoBuild | ,b``` führt abhängig vom Dateinamen ```:GoBuild``` oder ```:GoTestCompile``` aus
* ```:cnext | CTRL + x``` springt bei Fehlern im QuixFix Fenster zum nächsten Fehler
* ```:cprevious | CTRL + m``` springt bei Fehlern im QuixFix Fenster zum vorigen Fehler
* ```:cclose | ,a``` schließt das QuickFix-Fenster
* ```:GoCoverage``` zeigt die Testabdeckung an
* ```:GoCoverageClear``` blendet die Liste der Testabdeckungen aus
* ```:GoCoverageToggle``` schaltet zwischen ```:GoCoverage```  und ```:GoCoverageClear``` um
* ```:GoImport <package>```
* ```:GoImportAs <alias> <package>```
* ```:GoDrop <package>```
* ```:GImports```
* ```dif | daf``` löscht die innere / gesamte Funktion
* ```vif | vaf``` selektiert die innere / gesamte Funktion
* ```yif | yaf``` kopiert die innere / gesamte Funktion
* ```gS``` splittet eine Struct
* ```gJ``` fügt eine Struct zusammen
* ```:GoFmt``` formatiert aktuellen Quellcode, läuft automatisch beim Speichern
* ```:GoLint``` prüft den Quellcode nach den Lint Richtlinien
* ```:GoVet``` weist auf unsaubere Codepassagen hin
* ```:GoMetaLinter``` führt mehrere Lint Funktionen parallel aus
* ```:GoAlternate``` schaltet zwischen Programmcode und Testcode hin und her
* ```:GoDef | gd``` zeigt die Definition einer Funktion an
* ```:GoDefPop | CTRL + t```
* ```:GoDecls``` zeigt Deklarationen von Typen und Funktionen in der aktuellen Datei an
* ```:GoDeclsDir``` zeigt Deklarationen von Typen und Funktionen im aktuellen Verzeichnis an
* ```:GoDoc``` zeigt die Dokumentation zur Funktion unter dem Cursor an
* ```:GoInfo | ,i``` blendet die Signatur der Funktion unter dem Cursor ein
* ```:GoSameIds``` hebt alle Vorkommen des Begriffs unter dem Cursor optisch hervor
* ```:GoSameIdsClear``` hebt die Markierungen von ```:GoSameIds``` wieder auf
* ```:GoFiles``` zeigt alle go Dateien im aktuellen Verezeichnis an
* ```:GoDeps``` zeigt alle Dependencies der aktuellen Datei an
* ```:GoReferrers``` zeigt alle Referenzen des Artefakts unter dem Cursor m Workspace an
* ```:GoDescribe``` erweiterte Ansicht von ```:GoInfo```, zeigt Context des Artefakts unter dem Cursor
* ```:GoImplements``` zeigt die Interfaces, die ein Type implementiert
* ```:GoWhicherrs``` zeigt alle Konstanten, globalen Variablen und konkreten Typen, die als Werte von Errors auftreten können, gute Basis für's Error Handling
* ```:GoChannelPeers``` zeigt Sender und Empfänger eines Channels an, dazu muss beim Aufruf die ganze Zeile selektiert sein
* ```:GoCallees``` zeigt bei Aufruf über einem Funktionsaufruf den Definitionsort an
* ```:GoCallers``` zeigt bei Aufruf über einer Funktionsdefinition deren Aufrufe an
* ```:GoCallstack``` zeigt die Aufrufkette einer Funktion an
* ```:GoBuildTags``` setzt benutzerdefinierte Build Tags, lassen sich mit ```:GoBuildTags ""``` wieder löschen
* ```:GoRename <new>``` benennt alle Vorkommen des Wortes unter dem Cursor in _new_ um
* ```:GoAddTags json|xml|db``` fügt Tags zu einem Struct hinzu, Teil von _gomodifytags_
* ```:GoFreevars``` zeigt eine Liste aller Variablen, die refernziert werden, aber nicht deklariert wurden
* ```:GoGenerate``` automatisierte Code-Generierung bei der Compilierung, spannend, aber noch nicht weiter erforscht (c;
* ```:GoImpl``` generiert Methodenrümpfe für Implementierung von Interfaces
  * Cursor steht auf Type, Eingabe von ```:GoImpl``` öffnet einen Prompt
  * dort Objekt eingeben, dessen Interface man implementieren möchte
  * nach ```Enter``` wird Gerüst der Methoden generiert
  * geht auch an beliebiger Stelle im Code, z.B. mit ```:GoImpl b *B fmt.Stringer```

## vimtex

* ```:VimtexInfo``` ... Info über aktuelles LaTeX Projekt
* ```:VimtexTocOpen``` ... zeigt Inhaltsverzeichnis
* ```:VimtexTocToggle``` ... schaltet Inhaltsverzeichnis ein/aus
* ```:VimtexCompile``` ... compiliert aktuelle Datei
* ```:VimtexStop``` ... stoppt aktuellen Compilerlauf
* ```:VimtexClean``` ... räumt Nebenprodukte der Compilierung auf

## CoC

* ```gd``` gehe zur Definition einer Variablen oder Funktion
* ```gy``` gehe zur Type-Definition einer Variablen
* ```gi``` gehe zur Implementierung einer Funktion (unter Go mit ```gd```)
* ```gr``` listet alle Vorkommen / References einer Variablen oder Funktion

## NerdTree

* ```,n``` setzt Fokus auf den Tree
* ```CTRL + n``` blendet Tree ein
* ```CTRL + t``` blendet Tree aus
* ```CTRL + f``` sucht nach Dateien

## Tabs

* realisiert über BarBar
* jede über NerdTree geöffnete Datei wird in einem neuen Tab abgelegt
* ```ALT + .``` wechselt zum nächsten Tab
* ```ALT + ,``` wechselt zum vorherigen Tab
* ```ALT + c``` schließt den aktuellen Tab
* ```SPACE + bd``` sortiert die Tabs nach Directories
* ```SPACE + bb``` sortiert die Tabs nach ihrer BufferNumber
* ```SPACE + bl``` sortiert die Tabs nach Programmiersprachen
* ```SPACE + bw``` sortiert die Tabs nach ihrer WindowNumber

## Windows

* ```CTRL + w + v``` splittet vertikal
* ```CTRL + w + s``` splittet horizontal
* ```CTRL + Cursortasten``` wechselt zwischen Fenstern
* ```CTRL + w + >``` vergrößert die Breite des aktuellen Fensters
* ```CTRL + w + <``` reduziert die Breite des aktuellen Fensters
* ```CTRL + w + +``` vergrößert die Höhe des aktuellen Fensters
* ```CTRL + w + -``` reduziert die Höhe des aktuellen Fensters
* ```:bp``` wechselt einen Buffer nach links (unter der Annahme, dass pro Tab / Window ein anderer Buffer geöffnet ist)
* ```:bn``` wechselt einen Buffer nach rechts
* ```:b#``` wechselt zum vorigen Buffer, der mehrmalige Aufruf springt zwischen genau zwei Buffern hin und her
* ```:bd``` löscht den aktuellen Buffer
* ```:bd#``` löscht den vorigen Buffer

## Visual Mode

* ```v``` ... zeichenweiser Modus
* ```V``` ... zeilenweises Vorgehen
* ```CTRL + v``` ... blockweiser Ansatz