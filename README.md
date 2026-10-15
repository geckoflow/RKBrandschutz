# RK Brandschutztechnik – statische Website

Statische Version von <https://www.rk-brandschutz.at/>, die die bisherige WordPress-Installation ersetzt.
Kein PHP, keine Datenbank und keine Cookies. Externe Dienste werden nicht geladen: Alle Schriften,
Bilder, Styles und Skripte liegen im Repository.

## Struktur

```
index.html                Startseite (Slider, Leistungen, Zahlen, Partner-Logos)
home/                     Seite „Home“ (Menüpunkt „Home“)
ueber-uns/                Über uns
leistungen/               Leistungen
partnerbetriebe/          Partnerbetriebe
gallery/                  Galerie
kontakt/                  Kontakt
impressum/                Impressum
datenschutz/              Datenschutz
404.html                  Fehlerseite (ermittelt den Wurzelpfad selbst: „/“ oder auf GitHub Pages „/<Repo>/“)
assets/css/               Theme-CSS (Scapeshot Pro), WordPress-Block-Styles, Poppins-@font-face
assets/fonts/             Poppins (woff2) und Dashicons, lokal gehostet
assets/js/                jQuery, Owl Carousel, Theme-Skripte, config.js (Theme-Optionen)
assets/images/            Theme-Grafiken
assets/uploads/JJJJ/MM/   Bilder aus der WordPress-Mediathek (inkl. srcset-Größen)
robots.txt, sitemap.xml   Für Suchmaschinen
.htaccess                 Nur für Apache: 404-Seite, Umleitung alter /wp-content/uploads/-Pfade
```

Die URLs sind dieselben wie bei der WordPress-Seite (z. B. `/kontakt/`), bestehende Links und
Suchmaschineneinträge funktionieren also weiter. Innerhalb der Seiten werden relative Pfade verwendet,
deshalb lässt sich die Seite auch in einem Unterordner oder lokal über einen Webserver betreiben.

## Änderungen gegenüber der WordPress-Seite

- Cookie-Banner („Cookie Compliance“) samt Skript und Styles entfernt. Die Seite setzt keine Cookies
  und schreibt nichts in den Local- oder Session-Storage.
- WordPress-Emoji-Skript (lud Inhalte von `s.w.org`), REST-API-, oEmbed-, RSS- und XML-RPC-Links,
  Speculation Rules sowie die Skripte von Contact Form 7, Catch Infinite Scroll und Essential Widgets
  entfernt. Diese Plugins wurden auf keiner Seite tatsächlich verwendet.
- Die Suche wurde entfernt, weil sie ein WordPress-Backend braucht.
- Die von WordPress inline ausgegebenen Styles liegen jetzt in `assets/css/wp-core.css` und
  `assets/css/theme-custom.css`, die Theme-Optionen in `assets/js/config.js`.
- Das Copyright-Jahr im Footer wird per JavaScript aktuell gehalten.
- Kleinere Korrekturen: `lang="de"` am `<html>`-Element ergänzt, leeres Header-Bild und
  ins Leere führende Platzhalter-Links (`http://-`) bei „Das macht uns aus“ entfernt.

## Lokal ansehen

```sh
python3 -m http.server 8000
# dann http://localhost:8000/ öffnen
```

## Deployment

Den Inhalt des Repositorys (ohne `.git`) in das Web-Root des Hostings kopieren. Ein Build-Schritt ist
nicht nötig.

## Lizenzen der eingebundenen Komponenten

- Theme „Scapeshot Pro“ von Catch Themes: GPL v2 oder neuer
- jQuery und jQuery Migrate: MIT
- Owl Carousel 2: MIT
- jquery.matchHeight: MIT
- Dashicons (WordPress): GPL v2 oder neuer
- Schrift Poppins: SIL Open Font License 1.1
