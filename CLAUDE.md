# CLAUDE.md — OkeyMate Web

## Projekt-Übersicht

Statische Landing Page für die OkeyMate iOS-App.  
Gehostet auf GitHub Pages unter **okeymate.app**.  
Kein Framework, kein Build-Step — reines HTML/CSS/JS.

## Dateistruktur

```
okeymate-web/
├── index.html          # Haupt-Landing-Page (alles in einer Datei)
├── download/
│   └── index.html      # Smart Redirect → App Store / Play Store
├── assets/
│   └── icon.png        # App Icon 1024x1024
└── CNAME               # okeymate.app (von GitHub Pages gesetzt, nicht anfassen)
```

## Tech-Stack

- Reines HTML5 / CSS3 / Vanilla JS
- Keine Dependencies, kein npm, kein Build
- Google Fonts: Inter (über CDN)
- QR Code: qrcodejs (über CDN, cdnjs.cloudflare.com)
- Hosting: GitHub Pages (Branch: main, Folder: root)
- Domain: okeymate.app (IONOS, DNS zeigt auf GitHub Pages)

## Farbschema

Identisch zur iOS-App:
- `--blue:   #1C3F73`  — Primärfarbe (Nav, Buttons, Überschriften)
- `--orange: #E07820`  — Akzentfarbe (CTA-Button, Hover)
- `--light:  #f4f7fc`  — Hintergrund Features-Section
- `--white:  #ffffff`

## Mehrsprachigkeit

Alle Texte sind im `T`-Objekt in `index.html` definiert (unten im `<script>`-Block):
- `T.de` — Deutsch
- `T.tr` — Türkisch
- `T.en` — Englisch

Neue Texte immer in allen 3 Sprachen eintragen.  
Spracherkennung: automatisch via `navigator.language`, Auswahl wird in `localStorage` gespeichert.

## Store URLs — noch eintragen

In **beiden** Dateien müssen nach App-Veröffentlichung diese Platzhalter ersetzt werden:

```
index.html       → var IOS_URL     = "https://apps.apple.com/...";
index.html       → var ANDROID_URL = "https://play.google.com/...";
download/index.html → var IOS_URL     = "...";
download/index.html → var ANDROID_URL = "...";
```

## Deployment

Einfach pushen — GitHub Pages deployed automatisch:
```bash
git add -A
git commit -m "..."
git push
```

Änderungen sind nach ~1 Minute live auf okeymate.app.

## Wichtige Regeln

- CNAME Datei **niemals löschen oder bearbeiten** — bricht die Custom Domain
- Keine externen JS-Frameworks einführen — Seite bleibt dependency-frei
- QR Code zeigt immer auf `https://okeymate.app/download` (nicht direkt auf Store)
- `download/index.html` übernimmt die eigentliche Plattform-Erkennung und Weiterleitung

## Geplante Erweiterungen (Phase 2)

- Echte App Store / Play Store Links eintragen sobald App live
- Screenshot-Sektion mit echten App-Screenshots
- Datenschutz / Impressum Seite (für App Store Anforderungen)
