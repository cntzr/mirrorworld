---
title: Vifm
date: 2022-12-31
lastmod: 2022-12-31
tags: [ "linux","dateimanager" ]
---

Damit ist das Duo aus Dateimanager und Editor für den Alltag wieder 
komplett. Nach einem kurzen Ausflug zu _ranger_ bin ich sehr schnell 
wieder zu _vifm_ zurückgekehrt und habe mich durch einige Tutorials 
geschaut und gelesen. Das hat noch ein paar interessante Shortcuts offen 
gelegt. Damit sie alle an einer Stelle beisammen sind, schreibe ich 
sie hier auf ...

## Navigation

* ```j | k``` ... eine Datei oder ein Verzeichnis hoch bzw. runter
* ```h``` ... eine Verzeichnisebene zurück
* ```l``` ... wechselt in ein Verzeichnis oder öffnet eine Datei
* ```TAB | Space``` ... Wechsel zwischen den Panes

## Ansichten

* ```CTRL + w + v``` ... Anzeige der beiden Panes vertikal nebeneinander (Default)
* ```CTRL + w + s``` ... Anzeige der beiden Panes untereinander
* ```CTRL + w + o``` ... Anzeige von nur einem Pane, ```TAB``` wechselt das angezeigte Pane
* ```e``` ... Vorschau der selektierten Datei oder des Verzeichnisses im selben Pane, wird mit ```q``` beendet
* ```w``` ... Vorschau dere selektierten Datei oder des Verzeichnisses im gegenüberliegenden Pane
    * ```:view``` ... beendet die Vorschau
    * ```SHIFT + TAB``` ... wechselt während der Vorschau zwischen den Panes
* ```zo``` ... Dotfiles anzeigen
* ```zm``` ... DotFiles ausblenden

## Bearbeiten

* ```cw``` ... Editieren des selektierten Eintrags
* ```[n]yy``` ... kopiert _n_ Einträge in die Zwischenablage
* ```[n]dd``` ... verschiebt / löscht _n_ Einträge in die Zwischenablage
* ```p``` ... fügt Inhalt der Zwischenablage ein

## Commands

* beginnen mit einem Doppelpunkt
* ```:mkdir <directory>``` ... legt neues Verzeichnis an
* ```:touch <filename>``` ... legt eine neue Datei an
* ```:df``` ... Anzeige des freien Plattenplatzes

## Bookmarks

* ```m <char>``` ... legt einen Bookmark für das aktuell geöffnete (!) Verzeichnis an
* ```:marks``` ... zeigt alle definierten Bookmarks an, können dort auch bearbeitet werden
* ```'<char>``` ... ruft einen Bookmark auf

