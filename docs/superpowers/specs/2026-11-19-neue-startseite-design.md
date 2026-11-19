# Neue Startseite JFB Landschaftsbau: Design

Stand: 19.11.2026 · Entwurf zum Ansehen: Variante B, Runde 2 (Artifact „JFB Hero-Entwürfe“)

## Warum

Die jetzige `index.html` wirkt durch die schwarzen und fast schwarzen Bereiche (Kopf, Leistungen, Kontakt, Footer) zu großen Teilen dunkel. Schwarz ist die Markenfarbe von JFB und soll klar erkennbar bleiben, aber die Seite soll insgesamt hell wirken. Außerdem soll man sich am Handy schnell zurechtfinden.

## Ziele

- Gleiche Inhalte wie die heutige `index.html`: Hero, Über uns, vier Leistungen, drei Projekte mit Galerien, Kontakt, Footer mit Impressum und Datenschutz.
- Heller Grundton mit gezieltem Schwarz.
- Eine sehr gute Handy-Ansicht.

## Nicht-Ziele

- Keine neuen Inhalte, Seiten oder Projekte.
- Keine Build-Werkzeuge, kein Framework.
- Keine eigene Domain (alle Verweise bleiben auf `sebutd.github.io/jfb`).

## Was die Arbeit scheitern ließe (Anti-Ziele)

- Die Seite wirkt wieder überwiegend schwarz.
- Am Handy überlappt etwas, die Schrift ist zu klein oder man findet den Kontakt nicht.
- Es entstehen Verbindungen zu Drittanbietern, die heute nicht bestehen (Datenschutz). Formspree bleibt die einzige Ausnahme, wie heute.
- Was heute funktioniert, geht verloren: Galerie-Großansicht, Seite ohne JavaScript nutzbar, Tastaturbedienung, Angaben für Google und Teilen-Vorschau.

## Ansätze

1. **`index.html` auf dem Arbeitszweig neu schreiben** (gewählt). Eine einzelne Datei wie heute, GitHub Pages, vorhandene Bilder und Edo-Schrift. Die Live-Seite ändert sich erst beim Übernehmen nach `main`.
2. Parallel unter `/neu/` aufbauen. Verworfen: Dafür müsste die Seite vorher auf `main`, es gibt einen zweiten Umzugsschritt und eine Zeit lang doppelte Dateien.
3. Tailwind oder ein Seitengenerator. Verworfen: Das brächte einen Build-Schritt für eine Seite, die bewusst ohne auskommt.

## Vom Auftraggeber entschieden

- **Hero, Variante B:** Ein Projektfoto über die ganze Breite. Unten links sitzt ein massiver schwarzer Block mit Eyebrow („Klein Berssen · Emsland“), der Überschrift „Wir gestalten. Wir bauen. Wir bewegen.“, einem Untertitel und den Buttons „Projekt anfragen“ (grün) und „Unsere Arbeiten“ (Rahmen). Am Handy steht das Foto oben, der schwarze Block überlappt es von unten.
- **Wechselndes Titelbild:** Die Bilder blenden alle sechs Sekunden weich ineinander über. Die Reihenfolge ist
  1. `muehlenbau/8.webp` (fertiger Steinweg)
  2. `strassenbau/2.webp` (fertige Pflasterung)
  3. `abbruch/5.webp` (Bagger mit Sortiergreifer)

  Ein Schild nennt das aktuelle Projekt, Punkte zeigen an, welches Bild gerade läuft. Bei „Bewegung reduzieren“ steht das erste Bild still.
- **Kopf am Handy:** Nur das Logo, „JFB“ groß mit „LANDSCHAFTSBAU“ klein darunter, und ein Drei-Striche-Menü zum Aufklappen. Keine Sprungleiste. Im aufgeklappten Menü stehen Leistungen, Projekte, Über uns, Kontakt und ein grüner Button „Anrufen“.
- **Firmenname** überall in der Schrift Edo.
- **Kontakt:** Telefon, WhatsApp, E-Mail, Standort und Instagram bleiben. Das Formular bleibt, wird aber kürzer: Name, „Telefon oder E-Mail“, „Worum geht es?“. Es läuft weiter über Formspree mit dem bisherigen Datenschutzhinweis, Honeypot und Erfolgs- bzw. Fehlermeldung.
- **Farben:**
  - Schwarz `#0b0b0b` für Kopfleiste, Überschriften, Buttons, den Hero-Block und den Kontakt-Bereich
  - Betongrau `#eeeeea` als Grundfläche
  - Weiß für Karten
  - Logo-Grün `#3fd23a` nur als Akzent; als Textfarbe auf Hell eine dunklere Stufe für ausreichenden Kontrast

## Meine Entscheidungen (bitte prüfen)

- **Schriften:** Archivo für Überschriften und Inter für Text, so wie im Entwurf. Beide werden selbst gehostet, als WOFF2 mit lateinischem Zeichensatz unter `fonts/`. Damit entsteht keine Verbindung zu Google.
- **Reihenfolge der Abschnitte:** Hero, Leistungen, Projekte, Über uns, Kontakt. Leistungen und Projekte stehen vorn, weil Besucher die eher suchen. Heute steht „Über uns“ direkt nach dem Hero.
- **Dunkle Flächen:** Schwarz sind nur die Kopfleiste, der Hero-Block, der Kontakt-Bereich und der Footer. Leistungen, Projekte und Über uns sind hell.
- **Desktop-Kopf:** Logo mit Name, die Links rechts, „Kontakt“ als grüner Button.
- **Leistungen:** Vier Karten auf Weiß mit den vorhandenen Icons. Im Hero führen Leistungs-Chips zum Abschnitt.
- **Projekte:** Die Karten mit Wisch-Slider und die Großansicht (`<dialog>`) bleiben in der Funktion. Nur das Aussehen wird an das helle Design angepasst. Der `<noscript>`-Ersatz bleibt.
- **Bilder:** Hero-Bilder mit `srcset` aus `klein`, `mittel` und Original, der Ausschnitt ist pro Bild über `object-position` eingestellt. Das erste Bild lädt sofort, die anderen danach.
- **Impressum, Datenschutz und 404** bekommen über `rechtliches.css` dieselben hellen Farben und Schriften.
- `theme-color`, die Angaben für Google, die Teilen-Vorschau und das Manifest bleiben inhaltlich gleich.

## Offen für die Umsetzung

- Genaue Abstände, Schriftgrößen und Umbruchpunkte (Richtwert: Handy bis 768 px, Tablet bis 1024 px).
- Die Hover- und Fokus-Zustände im Detail.
- Prüfen mit Playwright: Handy (390 px), Tablet und Desktop, ohne JavaScript, mit Tastatur, kein seitliches Scrollen.
