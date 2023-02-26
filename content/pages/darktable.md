---
title: Darktable
date: 2023-02-11
lastmod: 2023-02-26
tags: [ "darktable", "pages", "workflow" ]
---

## Darktable

Ich verwende als primäres Archiv externe SSD's, durchweg Samsung T3 ... 
T7. Sie sind sprechend gelabelt und mit dazu passenden Aufklebern versehen. 
Fotos kopiere ich direkt von der Speicherkarte auf eine SSD. Die 
Ablagestruktur ist dort nach Jahren und Monaten gegliedert. Fotoreiche 
Monate gliedere ich zusätzlich nach Tagen oder Events.

### LightTable

Fotos importiere ich direkt von der gemounteten SSD (nicht über 
_kopieren und importieren_). Darktable speichert in der Datenbank auf 
dem Rechner nur Thumbnails der Fotos.

Fotos lassen sich im LightTable als lokale Kopie markieren. Ich kann sie 
später ohne externe Festplatte bearbeiten. 

Fotos erhalten beim Import als Standardbewertung 1 Stern. Ich stelle 
den  Filter auf 1 Stern und bewerte die gefilterten Fotos mit 0 oder 
2 Sternen. Dann stelle ich den Filter auf 2 Sterne und bewerte die 
gefilterten Fotos mit 0 oder 3 Sternen. Nun setze ich den Filter auf
3 Sterne. Wenn ich mir bei einem Foto nicht sicher bin, ob sich eine 
ernsthafte Bearbeitung lohnt, beginne ich es kurz zu bearbeiten. Die 
Fotos werden mit 0 oder 4 Sternen bewertet.

Jetzt stelle ich den Filter auf 4 Sterne und bearbeite die gefilterten 
Fotos final. Danach werden sie mit 5 Sternen bewertet. Damit signalisiere
ich, dass ihre Bearbeitung abgeschlossen ist. Fotos, die fertig 
bearbeitet wurden, exportiere ich mindestens als JPG in Web-tauglicher 
Auflösung.

Am Ende lösche ich alle Fotos mit einer Bewertung von 0 Sternen physisch 
von der SSD. Dies schließt auch die zugehörigen XMP Files ein.

### Darkroom

#### RAW Clippings erkennen

* mit ```SHIFT + o``` _raw overexposure check_ einschalten
* überbelichtete Passagen können über _highlight reconstruction_ (jetzt) ODER _filmic rgb_ (später) wiederhergestellt werden
* _raw overexposure check_ wieder ausschalten

#### Exposure

* mit ```CTRL + b``` _color assessment_ einschalten
* im _exposure_ Module die Helligkeit der Mitteltöne über den _exposure_ Regler so einstellen, dass sie dem hellen Grau des Hintergrunds entspricht
* helles Weiß im Foto sollte jetzt dem Weiß im Rahmen entsprechen
* zum _filmic rgb_ Module wechseln
* mit den Reglern für _white relative exposure_ und _black relative exposure_ die Lichter und Schwarztöne einstellen
* mit ```o``` die _clipping warnings_ aktivieren und wie folgt einstellen ...
  * clipping preview mode ... luminance only
  * color scheme ... red & blue
  * lower threshold ... -12.69 EV
  * upper threshold .. 99.99 %
* bei Bedarf Lichter und Schwarztöne dezent nachjustieren
* _color assessment_ und _clipping warnings_ ausschalten

#### RAW Clippings behandeln

* falls es beim _raw overexposure check_ überbelichtete Passagen gab, können diese nun im _filmic rgb_ Module unter dem Tab _reconstruct_ behandelt werden
* das _highlight reconstruction_ Module sollte an dieser Stelle deaktiviert sein
* nicht mit der Option _enable highlight reconstruction_ im aktuellen Tab verwechseln, die man durchaus ausprobieren kann
* die Rekonstruktion blendet die Übergänge zwischen überbelichteten Passagen und der Umgebung über, sie kann keine verlorenen Pixel ersetzen
* mit den Reglern spielen, dabei das Ergebnis beobachten
* die behandelten Bereiche lassen sich besser einschätzen, wenn die Maske aktiviert wird
* Einfärbungen in Magenta lassen sich mit dem Regler _gray/colorful details_ behandeln

#### Contrast

* im _filmic rgb_ Module zum _look_ Tab wechseln
* mit den Reglern für _contrast_ und _latitude_ rumspielen
* mit dem _tone equalizer_ Module und dessen _advanced_ Tab lassen sich einzelne Bereiche noch gezielter anpassen
* TODO ... _diffuse and sharpen_ Module ausprobieren ... [Tutorial](https://www.youtube.com/watch?v=pAbyORw0mng)

#### Color

* White Balance wird über das _color calibration_ Module gesetzt
* das gleichnamige Module gilt als deprecated
* im _CAT_ Tab eine zum Motiv passende Lichtquelle (Illuminant) auswählen
* alternativ einen mittleren Graubereich mit dem Color Picker markieren
* der _adaptation_ Value kann unverändert bleiben (default ist _Linear Breadford (1985)_)
* anpassen bei LED Licht oder Sonnenuntergängen
* über Masken lassen sich einzelnen Bereichen im Foto unterschiedliche White Einstellungen zuweisen

#### Saturation

* über das _color balance rgb_ Module im _master_ Tab einstellen
* Basis ist ...
  * global vibrance ... + 25 %
  * global chroma ... + 25 %
  * saturation ... 
    * shadows ... + 20 %
    * mid-tones ... + 10 %
    * highlights ... - 5 %
  * brilliance ...
    * global brilliance ... - 10 %
    * highlights ... + 10 %
* Kontrolle des Clippings mit ```o```

#### Color Adjustments

* weitere Farbanpassungen ...
  * _channel mixing_ Tabs im _color calibration_ Module
  * _color balance rgb_ Module
  * notfalls _color zones_ oder _color lookup table_ Module
* eins oder mehrere Module parallel einsetzen
* es sind auch mehrere Instanzen eines Modules für verschiedene Bereiche möglich

#### Black & White

* _color calibration_ Module mit _grey_ Tab ... [Tutorial](https://www.youtube.com/watch?v=Yg0pspIT0nE)
* _lookup table 3D_ mit einer schwarz-weißen LUT ... [freie Collections](https://www.reddit.com/r/DarkTable/comments/cyn5h1/darktable_collected_resources/)

#### Corrections

* _crop_ Module
* _rotate and perspective_ Module
* _diffuse or sharpen_ Module mit _dehaze_ Preset gegen Dunst in Landschaften
* _denoise (profiled)_ Module gegen Rauschen
* _chromatic abberations_ Module
* _hot pixels_ Module bei Langzeit- oder Nachtaufnahmen
* _retouch_ Module gegen rote Augen
