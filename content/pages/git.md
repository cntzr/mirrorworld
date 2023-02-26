---
title: Workflows
date: 2023-02-11
lastmod: 2023-02-26
tags: [ "git", "pages", "workflow" ]
---

## Git mit soft-serve

GitHub hat stolz verkündet, so und so viele Millionen registrierte Accounts
zu haben. Irgendwer meinte letztens in einem Blog, dass eigentlich für
jeden Anwendungszweck schon eine Applikation geschrieben sei. Man müsste
nur eine Suchmaschine mit den passenden Suchbegriffen füttern und könnte
sich die Entwicklung sparen. Allerdings muss ich dann mit der Sicht eines
anderen Entwicklers auf mein Problem leben. Will ich nicht, also werde ich
auch in Zukunft meine Apps selbst schreiben.

Generell wird immer mehr Content auf Plattformen ins Web gestellt, deren 
Fortbestand nicht gesichert ist. Selbst bei freien Anwendungen lässt es 
sich nicht verhindern, dass der Betreiber über Nacht den Laden dicht macht 
und die Daten verkauft. Ich kann meine Daten x Mal spiegeln, ich kann sie 
ins _Distributed Web_ stellen. Ich halte sie lieber auf meinem eigenen 
Server und sichere sie per Backup.

_Soft-serve_ ist ein Git Server von _Charm_. Er lässt sich nur über ssh 
ansprechen und verfügt über ein TUI. Das Interface greift auf _BubbleTea_ 
zurück. Das ist bereits von _glow_ bekannt. Ich mag es sehr.

Der Server läuft auf meinem Alltags-Notebook über einen _systemd user 
service_.

### TUI

Das Interface wird mit ```ssh -p 23231 localhost``` gestartet. Es bietet 
analog zu den klassischen UI's im Browsser Zugriff auf die wichtigsten 
Funktionen. Über das private _config_ Repository lassen sich Berechtigungen 
und die Eigenschaften der Repositories anpassen.

### Repositories

    take ~/dev/neues_repo

    git init
    git branch -m main

    touch LICENCE
    touch README.md
    touch .gitignore

    git add .
    git commit -m "initialer Commit"
    git remote add origin ssh:localhost:23231/neues_repo
    git push

----

## Git mit git

Auf dem remote Server ...

    take ~/repos/neues_repo.git

    git init --bare
    git branch -m main

Auf dem lokalen Client ...

    take ~/dev/neues_repo

    git init
    git branch -m main

    touch LICENCE
    touch README.md
    touch .gitignore

    git add .
    git commit -m "initialer Commit"
    git remote add origin server:repos/neues_repo.git
    git push

Die Schritte auf Server und Client wiederholen sich für jedes neue Repository.

