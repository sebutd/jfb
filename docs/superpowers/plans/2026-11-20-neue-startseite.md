# Neue Startseite Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Die neue helle Startseite (Variante B) ersetzt `index.html` und ist unter der Hauptadresse erreichbar. Die alte Seite wird archiviert.

**Architecture:** Eine einzelne statische `index.html` mit Inline-CSS und -JS, wie bisher, ausgeliefert über GitHub Pages von `main`. Schriften liegen selbst gehostet unter `fonts/`.

**Tech Stack:** HTML, CSS, Vanilla-JS, Playwright (nur zum Prüfen)

**Spec:** `docs/superpowers/specs/2026-11-19-neue-startseite-design.md`

## Global Constraints

- Keine Verbindungen zu Drittanbietern außer Formspree (`https://formspree.io/f/myeyqjrl`), Google-Maps-Link, WhatsApp- und Instagram-Links.
- Farben: Schwarz `#0b0b0b`, Betongrau `#eeeeea`, Weiß, Logo-Grün `#3fd23a` (nur Akzent).
- Firmenname in Edo (`fonts/edo.woff2`), Überschriften in Archivo, Text in Inter.
- Alle Verweise auf `https://sebutd.github.io/jfb/`.

## Review Focus

- Sehr schmale Handys (320 px): Name und Menü-Symbol dürfen nicht überlappen, kein seitliches Scrollen.
- Seite ohne JavaScript: Hero zeigt das erste Bild, Projekte zeigen Bilder (`<noscript>`), Menü erreichbar.
- „Bewegung reduzieren“: Titelbild wechselt nicht.
- Tastatur: Menü mit Escape schließen, Fokus sichtbar, Großansicht bedienbar.
- Formular: Fehler beim Senden zeigt Telefonnummer, Erfolg blendet Formular aus.

---

### Task 1: Alte Seite archivieren

**Files:** Create `archiv/2025/index.html` (Kopie der alten `index.html`, Pfade mit `../../` vorangestellt, `noindex`, kein Canonical). Modify `robots.txt` (`Disallow: /jfb/archiv/`).

- [ ] Kopieren, Pfade anpassen
- [ ] Prüfen: Playwright lädt `archiv/2025/index.html`, alle Bilder laden (keine 404)
- [ ] Commit

### Task 2: Schriften

**Files:** Create `fonts/archivo-700.woff2`, `fonts/archivo-800.woff2`, `fonts/inter-400.woff2`, `fonts/inter-600.woff2`, `fonts/OFL-archivo.txt`, `fonts/OFL-inter.txt` (latin-Subset aus `@fontsource`).

- [ ] Herunterladen, Lizenzen ablegen, Commit

### Task 3: Neue `index.html`

**Files:** Modify `index.html` komplett.

Abschnitte (IDs): `#hero`, `#leistungen`, `#projekte`, `#ueber`, `#kontakt`. JS-Funktionen aus der alten Seite unverändert übernommen: `slider()`, Projektkarten, `openOverlay()`, Formular-Submit. Neu: `heroWechsel()` (6000 ms, setzt `.on`, aktualisiert Beschriftung und Punkte, entfällt bei `prefers-reduced-motion`).

- [ ] Bauen
- [ ] Prüfen mit Playwright: 320, 390, 768, 1280 px; `scrollWidth <= innerWidth`; keine Konsolenfehler; Menü öffnen/schließen; ohne JS rendern
- [ ] Commit

### Task 4: Unterseiten hell

**Files:** Modify `rechtliches.css`, `404.html`.

- [ ] Farben und Schriften angleichen, Screenshot prüfen, Commit

### Task 5: Veröffentlichen

- [ ] Branch pushen, `main` per Fast-Forward aktualisieren und pushen (vom Auftraggeber freigegeben)
