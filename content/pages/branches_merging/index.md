---
title: Branches & Merging
date: 2022-09-09
lastmod: 2022-09-09
tags: [ "git" ]
draft: false
---

* alle Arbeiten zu Branches erfolgen aus demselben lokalen 
Repository-Verzeichnis heraus, es wird nichts extra geclont oder 
kopiert
* ```git checkout -b einbranch``` legt einen neuen Branch an, geht 
auch in zwei einzelnen Schritten mit ...
  * ```git branch einbranch```
  * ```git checkout einbranch```
* damit wird bereits deutlich, dass mit ```git checkout andererbranch``` 
der aktuelle Branch gewechselt wird
* vor dem Wechsel des Branches sollten alle lokalen Änderungen 
eingecheckt werden, egal, welchen Zustand sie gerade haben
* wenn die Arbeiten in einem Branch abgeschlossen sind, werden alle 
Änderungen zurück in den Master Branch gemergt
  * dazu wechselt man mit ```git checkout master``` in den gewünschten 
  Ziel Branch
  * ```git merge einbranch``` zieht die Änderungen aus dem Branch 
  _einbranch_ in den Master Branch, in dem wir uns gerade befinden
* ```git mergetool``` liefert grafische Unterstützung beim Merge, wenn 
es Konflikte gibt
* nicht mehr benötigte Branches sollten gelöscht werden, geht mit 
```git branch -d einbranch```

## Commit

* häufig committen, um Änderungen zu dokumentieren
* einzelne Dateien statt ganzer Verzeichnisbäume committen
* ```git add einedatei.bla``` fügt eine geänderte Datei zum Index eines 
späteren Commits hinzu
* ```git add .``` macht nach dem Rasenmäher-Prinzip dasselbe für alle 
geänderten Dateien im lokalen Repository-Verzeichnis
* letztere unbedarfte Variante lässt sich auch direkt in den Commit 
integrieren, der dann mit ```git commit -a -m "kannste schon so machen"``` 
läuft
* ```git commit -m "so ist es besser"``` führt einen normalen, autonomen 
Commit durch
* wenn man in einem Branch arbeitet, ist es üblich & hilfreich, am Ende 
des Kommentars die Bezeichnung des aktuellen Branches in eckigen Klammern 
hinzuzufügen ... etwa so ```git commit -m "Funktion XY ergänzt [sommer22]"```

## Links

* [Branching & Merching](https://git-scm.com/book/de/v2/Git-Branching-Einfaches-Branching-und-Merging)

