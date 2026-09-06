# Umsetzungsplan: Anmeldeseite „Weg des Wissens“

## 1. Auftrag und Ziel

Eine eigenständige, hochwertige und vollständig responsive Anmeldeseite für das Bildungsprogramm „Weg des Wissens“ erstellen. Die Seite richtet sich direkt an Interessierte, die das Programm verstehen, Vertrauen gewinnen und sich anschließend ohne Medienbruch registrieren möchten.

Die Seite wird als schlanke Astro-Webseite umgesetzt. Das bestehende Tally-Formular bleibt die einzige Quelle für die Erfassung und Verarbeitung der Anmeldedaten und wird als Standard-Embed direkt in die Seite integriert.

Primäres Ziel: Abschluss einer Anmeldung.

Sekundäre Ziele:

- Programm verständlich und seriös erklären
- Jahresbeitrag und Teilnahmeerwartungen transparent machen
- Fragen vor der Anmeldung beantworten
- freiwillige Spenden ermöglichen, ohne Anmeldung und Spende miteinander zu vermischen
- auf Smartphones besonders einfach nutzbar sein

## 2. Verbindliche Quellen und Links

### Logo

- Quelldatei: `/Users/aziz/Downloads/Logo/pngs/WDW LOGO 1.png`
- Format: PNG mit Transparenz, 1556 × 1388 Pixel, RGBA
- Bei der Umsetzung unverändert nach `public/images/wdw-logo.png` kopieren.
- Nicht nachzeichnen, umfärben oder verzerren.
- Für das sichtbare Logo sinnvollen Alternativtext verwenden: `Weg des Wissens`.
- Wenn das Logo direkt neben dem ausgeschriebenen Namen steht, leeren Alt-Text verwenden, um Dopplungen für Screenreader zu vermeiden.

### Anmeldung / Tally

- Öffentlicher Formularlink: <https://tally.so/r/yPQ996>
- Einbettung: Tally-Standard-Embed innerhalb des Abschnitts `#anmeldung`
- Für die endgültige Implementierung den aktuellen Embed-Code im veröffentlichten Tally-Formular unter `Share → Standard` kopieren, statt eine veraltete Variante fest einzubauen.
- Gewünschte Optionen: dynamische Höhe, 100 % Breite, möglichst transparenter Hintergrund, linksbündiger Formularinhalt und ausgeblendeter Formulartitel, sofern dadurch keine wichtigen Inhalte doppelt oder unsichtbar werden.
- Sichtbarer Fallback-Link direkt unter dem Embed: `Formular in einem neuen Fenster öffnen` → <https://tally.so/r/yPQ996>

Tally unterstützt einen Standard-Embed und eine dynamische Höhe. Änderungen am eigentlichen Formular werden danach automatisch im Embed sichtbar; geänderte Embed-Stile können einen erneuten Export des Codes erfordern.

### Noch bereitzustellende Quelle

- Die konkrete YouTube-URL des Vorstellungsvideos ist in dieser Übergabe nicht enthalten. Sie muss vor der Umsetzung aus dem vorhandenen Tally-Formular übernommen oder separat geliefert werden.

## 3. Zielgruppe und Tonalität

Zielgruppe sind deutschsprachige Interessierte, die sich selbst für das Bildungsprogramm registrieren möchten. Sie können bereits Vorwissen besitzen, sollen aber nicht voraussetzen müssen, wie das Programm organisatorisch funktioniert.

Ansprache:

- durchgehend per „du“
- ruhig, klar, respektvoll und verbindlich
- keine übertriebenen Versprechen
- keine aggressive Verkaufssprache
- islamische Begriffe nur verwenden, wenn sie für den Inhalt nötig sind; unbekannte Begriffe kurz verständlich einordnen

Gewünschtes Gefühl: `getragen · klar · vertrauenswürdig`.

## 4. Visuelle Leitlinie

Gewählte Richtung: helle Klarheit aus Entwurf B mit gezielten dunklen Abschnitten aus Entwurf A.

Szenensatz: Eine interessierte Person liest die Seite in ruhiger Umgebung auf dem Smartphone oder Laptop und möchte sich ohne Druck, aber mit vollständiger Klarheit für einen verbindlichen Bildungsweg entscheiden.

### Farbstrategie

Restrained bis Committed: Die Seite bleibt überwiegend neutral und hell; Gold und dunkle Flächen setzen gezielte Markenschwerpunkte.

- Marken-Gold: `#DFC186`
- Taupe/Graubraun: `#827763`
- Primärer dunkler Ton: ein fast schwarzer, leicht warmer Neutralton
- Heller Grund: neutrales Off-White ohne ausgeprägten Creme- oder Pergament-Look
- Fließtext: dunkler als Taupe, damit WCAG-AA-Kontrast erreicht wird

Die endgültigen CSS-Tokens sollen in OKLCH angelegt werden. Die Hex-Werte oben bleiben die verbindlichen visuellen Referenzen des Logos.

### Typografie

- Display/Überschriften: `Source Serif 4`, selbst gehostet als WOFF2
- Navigation, Fließtext, Buttons und Formularumfeld: `Manrope`, selbst gehostet als WOFF2
- Robuste System-Fallbacks definieren
- Überschriften mit `text-wrap: balance`, Fließtext mit `text-wrap: pretty`
- Lesebreite für längere Texte auf ungefähr 65–70 Zeichen begrenzen

Die Serifenschrift wird sparsam für Identität und Würde eingesetzt. Die Seite darf nicht wie ein Magazin oder eine Luxusmarke wirken.

### Formensprache

- klare Flächen und großzügige Abstände
- kleine bis mittlere Radien; keine Pillenform für alle Elemente
- feine Vollrahmen statt farbiger Seitenstreifen
- keine Glasflächen oder starken Schatten
- keine Verläufe
- keine islamischen Standardmotive wie Moschee-Silhouetten, Halbmonde oder Laternen
- falls ein Muster eingesetzt wird: sehr zurückhaltend aus der Geometrie des vorhandenen Logos ableiten
- keine endlosen, gleichförmigen Icon-Karten

### Bewegung

- höchstens eine ruhige, kurze Eröffnungschoreografie im Hero
- dezente Zustandswechsel bei Buttons und FAQ
- keine permanenten oder verspielten Animationen
- `prefers-reduced-motion` vollständig respektieren

## 5. Informationsarchitektur

Die Seite folgt einer einzigen linearen Entscheidungskette:

`Orientierung → Verständnis → Nutzen → Ablauf → Verbindlichkeit → offene Fragen → Anmeldung`

### 5.1 Kopfzeile

Inhalt:

- kompaktes WdW-Logo
- Ankerlinks: `Programm`, `Ablauf`, `Fragen`
- primärer Button: `Jetzt anmelden`

Verhalten:

- auf Desktop ruhig und kompakt
- auf Mobilgeräten keine überladene Navigation; höchstens Logo plus CTA
- CTA springt zu `#anmeldung`
- eine sticky Kopfzeile nur einsetzen, wenn sie auf kleinen Geräten nicht zu viel Höhe beansprucht

### 5.2 Hero

Zweck: sofort klären, was angeboten wird, für wen es gedacht ist und was der nächste Schritt ist.

Vorgeschlagener Inhalt:

- Logo deutlich sichtbar, aber nicht überdimensioniert
- H1: `Wissen, das dich weiterbringt.`
- Ergänzung: `Melde dich für das Weg des Wissens Bildungsprogramm an und vertiefe islamisches Wissen strukturiert, verständlich und gemeinsam mit anderen.`
- primärer CTA: `Jetzt anmelden`
- sekundärer Textlink: `Programm kennenlernen`
- kompakte Faktenzeile: `Strukturiertes Bildungsprogramm · Seminare und Begleitung · 100 € Jahresbeitrag`

Gestaltung: dunkle Hero-Fläche mit goldfarbenem Logo, heller Typografie und sehr zurückhaltender Logo-Geometrie als Hintergrundstruktur.

### 5.3 „Was ist Weg des Wissens?“

Zweck: Mission und Charakter des Programms knapp erklären.

Inhalt:

- kurze, verständliche Einführung in 2–3 Absätzen
- eingebettetes YouTube-Vorstellungsvideo
- Video nur nach Nutzerinteraktion laden oder über eine datenschutzfreundliche Einbettung (`youtube-nocookie.com`) integrieren
- klarer Play-Zustand mit verständlichem Datenschutzhinweis

### 5.4 „Was dich im Programm erwartet“

Inhalte in drei thematischen Gruppen statt in sieben identischen Karten:

1. `Fundament aufbauen`
   - islamische Grundlagen
   - Aqidah, Fiqh und islamisches Benehmen

2. `Verbindlich lernen`
   - Lernfortschritt, Aufgaben und Tests
   - Seminare mit Lehrern und Shuyukh

3. `Gemeinsam wachsen`
   - persönliche und religiöse Weiterentwicklung
   - gemeinsame Treffen und Aktivitäten
   - perspektivisch Arabisch und weiterführende Inhalte

Desktop: asymmetrische Textkomposition mit drei klar getrennten Bereichen. Mobil: gut lesbare lineare Abfolge.

### 5.5 „So läuft deine Anmeldung ab“

Eine echte Dreierschrittfolge, deshalb sind nummerierte Schritte hier sinnvoll:

1. `Informieren` – Inhalte, Beitrag und Erwartungen prüfen.
2. `Formular ausfüllen` – Kontaktdaten und verpflichtende Bestätigungen über Tally übermitteln.
3. `Nächste Schritte erhalten` – Bestätigung, Zahlungsinformationen und passende WhatsApp-Kontaktmöglichkeit auf der Tally-Dankeseite nutzen.

Keine falschen Aussagen zu Aufnahmegarantie, Bearbeitungszeit oder Unterrichtsbeginn ergänzen.

### 5.6 Beitrag und Teilnahmeerwartungen

Dieser Abschnitt steht auf einer dunklen Kontrastfläche und besteht aus zwei deutlich getrennten Spalten.

`Jahresbeitrag`

- klarer Betrag: `100 € pro Jahr`
- erläutern, wofür der Beitrag grundsätzlich steht, sofern dazu freigegebener Text vorliegt
- nicht als Monatsabo, Kaufpreis oder Spende bezeichnen

`Was wir von dir erwarten`

- regelmäßige und ernsthafte Teilnahme
- Bereitschaft zu Lernfortschritt, Aufgaben und Tests
- respektvoller Umgang
- klare Ablehnung von Extremismus und Gewaltverherrlichung
- Hinweis, dass die verbindlichen Bestätigungen im Formular erfolgen

Der Extremismus-Hinweis soll sachlich und eindeutig sein, nicht alarmistisch oder gestalterisch wie eine Warnmeldung erscheinen.

### 5.7 Freiwillig unterstützen

Eigenständiger, sekundärer Abschnitt. Die Spende darf visuell nicht mit der verpflichtenden Anmeldung oder dem Jahresbeitrag verwechselt werden.

Vorgeschlagene Überschrift: `Du möchtest Weg des Wissens zusätzlich unterstützen?`

Vorgeschlagener Text: `Unabhängig von deiner Anmeldung kannst du die Bildungsarbeit von Weg des Wissens e. V. jederzeit mit einer freiwilligen Spende unterstützen. Bitte gib bei der Überweisung als Verwendungszweck „Spende“ an.`

Bankverbindung:

- Empfänger: `Weg des Wissens e.V.`
- IBAN: `DE05 3705 0299 0000 7851 50`
- BIC: `COKSDE33XXX`
- Bank: `Kreissparkasse Köln`
- BLZ: `37050299`
- Verwendungszweck für freiwillige Spenden: `Spende`

Interaktion:

- IBAN und Verwendungszweck jeweils mit zugänglicher Kopierfunktion versehen
- nach dem Kopieren kurze Statusmeldung über eine `aria-live`-Region
- ohne JavaScript bleiben alle Angaben vollständig sichtbar und auswählbar
- keine Behauptung zur steuerlichen Absetzbarkeit oder Spendenbescheinigung aufnehmen, solange diese nicht ausdrücklich bestätigt wurde

### 5.8 FAQ

Native, zugängliche `details`/`summary`-Elemente verwenden. Vorgesehene Fragen:

- `Für wen ist das Bildungsprogramm geeignet?`
- `Welche Vorkenntnisse brauche ich?`
- `Was kostet die Teilnahme?`
- `Welche Teilnahme wird von mir erwartet?`
- `Wie geht es nach dem Absenden des Formulars weiter?`
- `Wo finde ich die WhatsApp-Kontakte?`
- `Kann ich Weg des Wissens auch unabhängig von einer Anmeldung unterstützen?`
- `Wie werden meine Daten verarbeitet?`

Antworten nur mit bestätigten Tatsachen formulieren. Ungeklärte Details als redaktionelle TODOs markieren, nicht erfinden.

### 5.9 Anmeldung / Tally-Embed

Der wichtigste Abschlussbereich erhält die ID `anmeldung`.

Aufbau:

- klare Überschrift: `Jetzt zum Bildungsprogramm anmelden`
- kurzer Erwartungssatz: `Halte deine Kontakt- und Adressdaten bereit und nimm dir einige Minuten Zeit für das Formular.`
- eingebettetes Tally-Formular auf voller verfügbarer Inhaltsbreite
- sichtbarer Ladezustand/Skeleton nur, wenn technisch zuverlässig
- verständlicher Fehlerzustand, falls das externe Formular blockiert wird
- Fallback-Button: `Formular direkt bei Tally öffnen`

Das Embed selbst darf nicht in eine kleine Karte gezwängt werden. Es soll wie der natürliche Abschluss der Seite wirken und auf Mobilgeräten ohne horizontales Scrollen funktionieren.

### 5.10 Abschluss und Footer

- WdW-Logo in kleiner Variante
- Kurzsatz zum Bildungsprogramm
- Links: `Datenschutz`, `Impressum`, `Zum Formular`
- optional Kontaktadresse, falls offiziell vorhanden
- keine WhatsApp-Telefonnummern zusätzlich im öffentlichen Footer zeigen; die zielgruppenspezifischen Links bleiben wie geplant auf der Tally-Dankeseite

## 6. CTA-System

Primärer CTA überall: `Jetzt anmelden` → `#anmeldung`.

Sekundäre Aktionen:

- `Programm kennenlernen` → `#programm`
- `Formular in einem neuen Fenster öffnen` → Tally-Link
- Kopieraktionen im Spendenabschnitt

Es gibt keinen konkurrierenden Spenden-CTA im Hero. Die freiwillige Unterstützung bleibt klar sekundär.

## 7. Tally-Dankeseite und Übergang

Die bestehende Tally-Dankeseite bleibt Teil des Ablaufs und enthält:

- Bestätigung der Anmeldung
- Bankverbindung
- WhatsApp-Link für Brüder: `0179 2321620`
- WhatsApp-Link für Schwestern: `0172 2955008`
- Hinweis für Schwestern, sich zusätzlich kurz per Sprachnachricht vorzustellen

Vor Veröffentlichung prüfen:

- Telefonnummern als funktionierende `wa.me`-Links mit deutschem Ländercode `49` und ohne führende Null
- Linktexte erklären klar, für wen der jeweilige Kontakt gedacht ist
- Dankeseite unterscheidet den Jahresbeitrag von einer freiwilligen Spende
- für freiwillige Spenden steht ausdrücklich der Verwendungszweck `Spende`

## 8. Technische Architektur

### Grundsetup

- Astro mit TypeScript
- statische Ausgabe, sofern keine serverseitige Funktion benötigt wird
- keine UI-Bibliothek
- kein clientseitiges Framework wie React/Vue/Svelte
- nur kleine, gezielte Vanilla-JavaScript-Inseln für Tally-Initialisierung und Kopierfunktionen
- möglichst keine unnötigen Laufzeitabhängigkeiten

### Vorgeschlagene Struktur

```text
/
├── public/
│   ├── fonts/
│   ├── images/
│   │   └── wdw-logo.png
│   ├── favicon.svg
│   └── og-image.jpg
├── src/
│   ├── components/
│   │   ├── SiteHeader.astro
│   │   ├── Hero.astro
│   │   ├── ProgramOverview.astro
│   │   ├── ProgramContents.astro
│   │   ├── EnrollmentSteps.astro
│   │   ├── ContributionExpectations.astro
│   │   ├── DonationSection.astro
│   │   ├── Faq.astro
│   │   ├── TallyEmbed.astro
│   │   └── SiteFooter.astro
│   ├── layouts/
│   │   └── BaseLayout.astro
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       ├── tokens.css
│       └── global.css
├── astro.config.mjs
├── package.json
└── tsconfig.json
```

Wenn die Seite wirklich nur aus einer Route besteht, dürfen kleine rein präsentative Abschnitte direkt in `index.astro` bleiben. Keine künstliche Komponentenzerlegung.

### Tally-Integration

- Tally-Skript nur einmal und möglichst verzögert laden
- iframe mit aussagekräftigem `title`
- `loading="lazy"`, sofern der Embed zuverlässig initialisiert
- Breite 100 %, keine horizontale Scrollbar
- dynamische Höhe aktivieren
- CSP/Datenschutzkonzept für `tally.so` und gegebenenfalls Tally-Unterdomains berücksichtigen
- bei Skriptblockade muss der direkte Formularlink funktionieren

### Inhaltspflege

Texte, FAQ, Kontodaten und externe Links in einer zentralen TypeScript-Konfiguration oder klar abgegrenzten Datenstruktur sammeln. Dadurch lassen sich Angaben ändern, ohne mehrere Komponenten durchsuchen zu müssen.

## 9. Responsive Verhalten

Mobile-first entwickeln.

- Hauptbreite für Inhalte etwa 1120–1200 px, Textspalten deutlich schmaler
- kleine Geräte ab ca. 320 px ohne horizontales Scrollen unterstützen
- CTA-Flächen auf Mobilgeräten mindestens 44 × 44 px
- Hero-Logo und H1 dürfen auf schmalen Geräten weder abgeschnitten werden noch umbrechende Einzelwörter erzeugen
- Zweispaltenbereiche unter ungefähr 760–840 px linear stapeln
- Bankdaten umbrechbar und zugleich gut kopierbar darstellen
- Tally-Embed auf realen iOS- und Android-Viewportgrößen prüfen

## 10. Barrierefreiheit und Datenschutz

- Ziel: WCAG 2.2 AA
- semantische Überschriftenhierarchie, genau eine H1
- sichtbare Tastaturfokusse
- Textkontrast mindestens 4,5:1; große Texte mindestens 3:1
- Navigation und FAQ vollständig per Tastatur bedienbar
- Sprunglink `Zum Inhalt`
- Animationen bei reduzierter Bewegung deaktivieren
- Logo korrekt beschreiben, dekorative Muster vor Screenreadern verbergen
- externe Inhalte klar kennzeichnen
- Datenschutzerklärung und Impressum müssen vor Go-live vorhanden und korrekt verlinkt sein
- Tally, YouTube und gegebenenfalls Webfonts im Datenschutz-/Consent-Konzept berücksichtigen
- bevorzugt selbst gehostete Fonts, um unnötige externe Anfragen zu vermeiden

## 11. SEO und Metadaten

- Seitentitel: `Anmeldung | Weg des Wissens`
- Meta-Description: kurze sachliche Beschreibung des Bildungsprogramms und der Anmeldung
- Canonical URL erst eintragen, wenn die endgültige Domain feststeht
- Open-Graph-Bild aus dem WdW-Logo und der Markenpalette erstellen
- Favicon aus dem isolierten Signet ableiten, ohne die ursprüngliche Logo-Datei zu verändern
- strukturierte Daten nur einsetzen, wenn Organisation, Angebot und Kontaktdaten vollständig bestätigt sind
- `noindex` während einer öffentlichen Vorschau erwägen; vor Go-live entfernen

## 12. Performance-Ziele

- möglichst wenig JavaScript außerhalb des Tally-Embeds
- Logo in sinnvoller Darstellungsgröße ausliefern; PNG komprimieren, Original als Quelle erhalten
- moderne Bildvariante optional zusätzlich als WebP/AVIF erzeugen, ohne Transparenzfehler
- Fonts auf tatsächlich benötigte Schnitte und Zeichensätze begrenzen
- Zielwerte: LCP unter 2,5 s, CLS unter 0,1, INP unter 200 ms unter realistischen Bedingungen
- externe Tally- und YouTube-Inhalte dürfen den initialen Seitenaufbau nicht blockieren

## 13. Inhaltliche TODOs vor oder während der Umsetzung

- genaue YouTube-URL übernehmen
- finalen Wortlaut der WdW-Kurzbeschreibung freigeben
- Details zu Voraussetzungen/Vorkenntnissen für FAQ bestätigen
- Ablauf nach der Anmeldung und mögliche Bearbeitungszeit bestätigen
- offizielle Kontaktadresse für den Footer klären
- finale Links für Impressum und Datenschutz bereitstellen
- klären, welcher Verwendungszweck für den verpflichtenden Jahresbeitrag gilt; `Spende` gilt ausdrücklich nur für freiwillige Spenden
- prüfen, ob Spendenbescheinigungen ausgestellt werden; bis zur Bestätigung keine Aussage dazu veröffentlichen
- endgültige Domain und Hosting-Ziel festlegen

## 14. Umsetzungsreihenfolge für den neuen Chat

1. Diesen Plan vollständig lesen und als verbindlichen Scope behandeln.
2. Projektstatus und vorhandene Dateien prüfen; bestehende Nutzeränderungen erhalten.
3. Astro-Grundgerüst ohne unnötige Integrationen anlegen.
4. Logo unverändert in den Projekt-Assetordner übernehmen.
5. Design-Tokens, Typografie und globale Layoutregeln umsetzen.
6. Seite semantisch in der oben definierten Reihenfolge bauen.
7. aktuellen Tally-Standard-Embed integrieren und Fallback-Link ergänzen.
8. YouTube datenschutzbewusst integrieren, sobald die URL vorliegt.
9. FAQ, Spendenbereich und zugängliche Kopierfunktionen fertigstellen.
10. mobile Darstellung, Tastaturnutzung, Kontrast und reduzierte Bewegung prüfen.
11. Produktion bauen und lokale Vorschau auf Fehler, Layoutverschiebungen und externe Einbettungen testen.
12. Desktop- und Mobile-Screenshots erstellen und einen visuellen Feinschliff durchführen.
13. Erst nach ausdrücklicher Freigabe veröffentlichen; kein Deployment, DNS-Wechsel oder Go-live während der reinen Umsetzung.

## 15. Abnahmekriterien

Die Seite ist fertig zur Freigabe, wenn:

- das originale WdW-Logo scharf, unverzerrt und prominent eingebunden ist
- das Programm innerhalb weniger Sekunden verständlich wird
- jeder primäre CTA zuverlässig zum Anmeldeformular führt
- das Tally-Formular direkt auf Desktop und Mobil funktioniert
- der direkte Tally-Link als Fallback vorhanden ist
- 100 € eindeutig als Jahresbeitrag bezeichnet werden
- die freiwillige Spende klar vom Jahresbeitrag getrennt ist
- bei Spenden der Verwendungszweck `Spende` sichtbar hervorgehoben ist
- Kontodaten korrekt und zugänglich kopierbar sind
- Extremismus- und Teilnahmehinweise sachlich und eindeutig dargestellt werden
- keine horizontalen Überläufe oder abgeschnittenen Inhalte auftreten
- Tastaturnavigation, Fokuszustände und Kontraste WCAG-AA-tauglich sind
- YouTube und Tally datenschutzbewusst eingebunden oder klar als externe Inhalte behandelt werden
- Impressum und Datenschutz erreichbar sind
- Produktions-Build fehlerfrei durchläuft
- keine Veröffentlichung ohne ausdrückliche Freigabe erfolgt

## 16. Kompakter Startprompt für den neuen Chat

> Setze die Anmeldeseite „Weg des Wissens“ nach dem vollständigen Plan in `WDW-ANMELDESEITE-PLAN.md` als schlanke Astro-Webseite um. Prüfe zuerst den bestehenden Projektstand und erhalte alle vorhandenen Nutzeränderungen. Verwende das Logo aus `/Users/aziz/Downloads/Logo/pngs/WDW LOGO 1.png` unverändert und integriere das Tally-Formular <https://tally.so/r/yPQ996> direkt in die Seite, inklusive sichtbarem Fallback-Link. Arbeite mobil-first, barrierearm und datenschutzbewusst. Implementiere auch den getrennten Spendenabschnitt mit der angegebenen Bankverbindung und dem verpflichtenden Verwendungszweck „Spende“. Führe lokale Build-, Responsive- und Accessibility-Prüfungen durch. Nicht deployen oder veröffentlichen.
