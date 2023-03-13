---
title: PostgreSQL
date: 2023-01-29
lastmod: 2023-01-29
tags: [ "datenbank" ]
---

Wenn ich im Web nachschlagen muss, wie ich an die Datenbank auf meinem 
Server rankomme, wird es höchste Zeit, das hier festzuhalten. Und ein 
paar andere wissenswerte Dinge gibt es da bestimmt auch noch, wenn ich 
erst mal mit dem Schreiben begonnen habe.

* ```psql -U postgres``` ... loggt den aktuellen User im Terminal als Superuser in die Shell von PostgreSQL ein

## Nützliches in der Shell

* ```\du``` ... listet die vorhandenen User auf
* ```\du+``` ... ergänzt die Userliste um eine Beschreibung

## Wissenswertes

Gibt man beim Anlegen einer Tabelle kein Schema an, wird die Tabelle 
im Standardschema *public* angelegt.

Im *public* Schema ...

> CREATE TABLE name(...);

In einem dedizierten Schema ...

> CREATE TABLE schema.name(...);

Das aktuelle Schema wird ermittelt mit ...

> SELECT current_schema();

Den aktuellen Search Path finde ich mit ...

> SHOW search_path;

Ein neues Schema lege ich an mit ...

> CREATE SCHEMA name;

Den Search Path kann ich setzen mit ...

> SET search_path TO name, public;

## Links

* [PostgreSQL Tutorial](https://www.postgresqltutorial.com/)
* [PostgreSQL Dokumentation](https://www.postgresql.org/docs/)
