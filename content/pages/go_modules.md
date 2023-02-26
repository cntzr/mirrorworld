---
title: Go Modules
date: 2023-02-26
lastmod: 2023-02-26
tags: [ "go", "pages", "workflow" ]
---

# Go Modules

Die Entwickler von Go haben damals entschieden, dass Importe von 
Packages immer mit full-qualified Pathes erfolgen sollen. Relative
Pfade und damit lokale Packages sind verpönt. Heißt in der Praxis, 
dass ich meine selbst geschriebenen Packages und Libraries auf 
irgendeinem Git Server hinterlegen muss. Ich kann die Sichtbarkeit 
über ein privates Repository einschränken. Um den Git Server käme 
ich nicht herum ...

... wenn dies eine der ganz seltenen Regeln ohne Ausnahme wäre (c; 
So kann ich aber mit Hilfe von Modulen und _replace's_ lokale 
Packages mit relativen Pfaden einbinden.

Hier ein Beispiel ...

* project_weather
  * cmd
    * go.mod
    * main.go
  * go.mod
  * README.md
  * weather
    * go.mod
    * weather.go
    * weather_test.go

Meine Packages bekommen wie gewohnt ganz normale Namen, hier _weather_ 
und _main_. Dass das _main_ Package in einem _wetter_ Module in einem 
Verzeichnis namens _cmd_ steht, spielt hier keine Rolle.

Jedes Package steht in einem eigenen Verzeichnis, soweit auch nichts
Neues. In jedem Verzeichnis erstelle ich eine Datei _go.mod_.

Inhalt der _go.mod_ im Verzeichnis _weather_ ...

    module example.org/weather
    go 1.20
    require github.com/irgend/ein/package vx.y.z

Der Import meines Packages in der _main.go_ erfolgt über 
```import example.org/weather```. Inhalt der _go.mod_ im Verzeichnis 
_cmd_ ...

    module example.org/cmd
    go 1.20
    require example.org/weather v0.0.0
    replace example.org/weather => ../weather

Inhalt der _go.mod_ im _Root_ Verzeichnis des Projektes ...

    module example.org/root
    go 1.20
    require example.org/weather v0.0.0
    replace example.org/weather => ./weather
    
Die _go.mod_ im _Root_ Verzeichnis hat lediglich eine Komfortfunktion.
Ich kann damit das Binary auch von dieser Ebene aus bauen. Baue ich immer 
nur im Verzeichnis _cmd_, kann diese _go.mod_ entfallen.
