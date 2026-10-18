# Salina Schmid – Coaching und Beratung

Statische Website (eine Seite) für Salina Schmid, Coaching und Beratung in Fahrwangen.

## Projektstruktur

```
index.html                     Die gesamte Seite (Home, Über mich, Kontakt)
assets/css/style.css           Styles, Design-Tokens als CSS-Variablen
assets/images/                 Ausgelieferte Bilder (JPEG + WebP, je zwei Breiten)
assets/images/source/          Originalbilder aus dem Design-Export (nicht ausgeliefert)
.github/workflows/static.yml   Deployment auf GitHub Pages
```

Die Seite kommt ohne Build-Schritt und ohne Abhängigkeiten aus: HTML und CSS werden
unverändert ausgeliefert. Schriften (Newsreader, DM Sans) werden von Google Fonts geladen.

## Lokal starten

```bash
python3 -m http.server 8000
```

Danach http://localhost:8000 öffnen.

## Deployment

Jeder Push auf `main` veröffentlicht das Repository-Root über GitHub Pages
(`.github/workflows/static.yml`). Es ist kein Build-Schritt nötig.

## Bilder neu erzeugen

Die ausgelieferten Bilder sind aus `assets/images/source/` abgeleitet
(JPEG mit Qualität 82 und WebP mit Qualität 80, jeweils in zwei Breiten).
Einmalig mit [sharp](https://sharp.pixelplumbing.com/) erzeugt, z. B.:

```bash
npx --yes sharp-cli --input assets/images/source/hero.png --output assets/images/ resize 1672
```

Bildausschnitte stammen aus dem Design: Das Hero-Bild ist rechtsbündig beschnitten
(`object-position: 100% 50%`), das Porträt zentriert.
