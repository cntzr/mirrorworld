---
title: Mono Repo
date: 2023-02-26
lastmod: 2023-03-10
tags: [ "go" ]
---

# Mono Repository

Die Entwickler von Go haben damals entschieden, dass Importe von 
Packages immer mit full-qualified Pathes erfolgen sollen. Relative
Pathes und damit lokale Packages sind verpönt. Heißt in der Praxis, 
dass ich meine selbst geschriebenen Packages auf irgendeinem Git 
Server hinterlegen muss. Ich kann die Sichtbarkeit über ein 
privates Repository einschränken. Um den sichtbaren Git Server käme 
ich nicht herum ...

... wenn dies eine der ganz seltenen Regeln ohne Ausnahme wäre (c; 
Ich kann mit Hilfe von Modules und _replace's_ lokale Packages mit 
relativen Pfaden einbinden.

Hier ein Beispiel ...

```
./datetimes
├── cmd
│   ├── go.mod
│   └── main.go
└── datetimes
    ├── datetimes.go
    └── go.mod
```

Meine Packages bekommen weiterhin normale Namen, hier _main_ (im 
Directory _cmd_) und _datetimes_. In jedem Directory erstelle ich 
eine Datei _go.mod_.

Die _go.mod_ von _datetimes_ sieht in etwa so aus ...

    module example.org/datetimes/datetimes
    go 1.20
    require github.com/irgend/ein/package vx.y.z

In der _main.go_ importiere ich das Package mit ...

    import example.org/datetimes/datetimes

Das provoziert vom Compiler eine Fehlermeldung, dass auf _example.org_ 
niemand ein Package namens _datetimes_ bereitstellt. Damit hat er 
Recht, denn das Package existiert nur auf meinem Server. Um den Compiler 
zu besänftigen, bedarf es einer weiteren _go.mod_ für _cmd_. Die sieht 
so aus ...

    module example.org/datetimes/cmd
    go 1.20
    require example.org/datetimes/datetimes v0.0.0
    replace example.org/datetimes/datetimes => ../datetimes

Das _vim-go_ Plugin im _neovim_ oder _gopls_ im Hintergrund empfehlen nun 
die Einrichtung eines Workspaces. Gibt es seit Go 1.18. Das Module 
_datetimes_ steht gemeinsam mit anderen Modules und Projekten in einem 
Parent Directory. Dieses Directory ist gleichzeitig das Root meines Mono 
Repositories. Denn eigentlich finde ich Git ja cool!

Die Struktur meines Mono Repositories sieht ungefähr so aus ...

```
mono
├── .git
├── datetimes
│   ├── cmd
│   │   ├── go.mod
│   │   └── main.go
│   └── datetimes
│       ├── datetimes.go
│       └── go.mod
├── dot
│   ├── cmd
│   │   ├── go.mod
│   │   └── main.go
│   ├── dot
│   │   ├── dot.go
│   │   ├── dot_test.go
│   │   └── go.mod
│   └── README.md
├── .gitignore
├── go.work
└── README.md
```

Das Directory _.git_ und die Datei _.gitignore_ sind reguläre Artefacts 
von Git. Das Repository hoste ich mit _Soft Serve_ von _Charm_ auf meinem 
eigenen Server. Den Workflow habe ich 
[hier](http://localhost:1313/pages/git) beschrieben.

Den Workspace bilde ich über die Datei _go.work_ ab. Sie lässt sich 
im Root Directory einrichten mit ...

    go work init
    go work use .datetimes/datetimes ./dot/dot

Ich erstelle und pflege den Inhalt manuell ...

    go 1.20
    use (
        ./datetimes/datetimes
        ./dot/dot
    )

Builds und Tests starte ich aus dem Root Directory ...

    go test ./dot/dot
    go run ./datetimes/cmd/main.go
    go run ./dot/cmd/main.go
