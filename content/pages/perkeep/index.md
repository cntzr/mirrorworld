---
title: Perkeep
date: 2023-01-30
date: 2023-01-30
tags: [ "archiv" ]
draft: false
---

## Binaries

Es gibt noch ein paar mehr Binaries, für die ich aber in meinem Alltag 
bislang keine Verwendung habe.

* perkeepd
  * -openbrowser=false ... default ist true, startet UI im Browser
  * -configfile=pfad\_zur\_config\_datei ... Angabe einer alternativen 
  Konfiguration
  * -keep-going ... Fortsetzung nach Reindizierung oder Recovery Errors
  * -listen string ... host:port to listen on, or :0 to auto-select. If 
  blank, the value in the config will be used instead.
  * -recovery int ... 
    * Recovery modes ... it corresponds for now to the recovery modes 
    of the blobpacked package. 
    * Which means ... 0 does nothing, 1 rebuilds the blobpacked index 
    without erasing it, and 2 wipes the blobpacked index before rebuilding 
    it.
    * -reindex ... reindiziert alle Blobs beim Start
* pk ... Schweizer Taschenmesser
* pk-get ... lädt Content von einem Server, besser mit *pk-mount*
* pk-mount ... verbindet zu einem Share

```bash
mkdir mountpoint
pk-mount mountpoint
cd mountpoint
exa -la
```

* pk-put ... lädt Dateien, Blobs oder Permanodes auf einen Server

## Konfiguration

Für den Server *perkeepd* gibt es eine simple und eine 
Low-Level-Konfiguration. Die simple Konfiguration wird beim Aufruf von 
*perkeepd* automatisch als *~/.config/perkeep/server-config.json* 
generiert, sofern sie nicht vorhanden ist. Die Low-Level-Variante ist 
sehr komplex, eine manuelle Erstellung wird daher explizit nicht 
empfohlen! Sie kann im Browser unter der URL 
http://localhost:3179/debug/config angezeigt werden. Von dort aus lässt 
sie sich kopieren und als *server-config.json* speichern. Der Wert des 
auth-Keys muss auf *localhost* geändert werden.

Für die Replikation auf eine weitere Perkeep-Instanz ist zwingend eine 
Low-Level-Konfiguration erforderlich. Hier ist dann der Eintrag 
*"handlerConfig": true* erforderlich, damit der Server die Konfiguration 
als Low-Level ansieht.

Die Konfiguration der Clients lässt sich mit ```pk-put init``` generieren. 
Dies sollte nach dem ersten Aufruf von *perkeepd* erfolgen, damit derselbe 
PGP-Key verwendet wird. Wenn mit Replicas gearbeitet wird, sollte die 
*client-config.json* jeweils einen Eintrag für jede Server-Instanz 
enthalten, damit die CLI's Aktionen mit den anderen Servern ausführen 
können.
