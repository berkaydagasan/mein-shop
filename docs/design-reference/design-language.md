# carbiente – Design-Sprache

> **Verbindliche Referenz** für jeden UI- und Design-Schritt im Theme `mein-shop/` (Shopify Skeleton Theme).
> Prüfinstanz ist der Sub-Agent [`design-language-guardian`](../../.claude/agents/design-language-guardian.md).
> Inspirationsquelle (nur Prinzipien): [hydrozz-analysis.md](hydrozz-analysis.md).
>
> **Stand:** 2026-10-05 (nach Schritt 7) · **Gilt für:** alle Sections, Blocks, Snippets, `critical.css`, `css-variables.liquid`, Templates.
> Bestehende Tokens bleiben die Quelle der Wahrheit. Dieses Dokument beschreibt, **wie** sie eingesetzt werden, und markiert Ergänzungen ausdrücklich als *Vorschlag*.

---

## 0. Kurzfassung (die 10 Regeln)

1. **Hell ist die Basis, Dunkel ist die Bühne.** Helle Sections erklären, dunkle „Nachtbühnen“ inszenieren. Pro Seite höchstens drei Nachtbühnen, nie mehr als zwei direkt hintereinander.
2. **Ein Akzent: Midnight Cyan.** `#006F86` auf hell, `#3DD5EE` auf dunkel. Keine zweite Akzentfarbe, keine Verläufe zwischen Farben.
3. **Licht ist unser Motiv, nicht unsere Deko.** Glow und Lichtlinie stehen nur auf dunklen Flächen, sparsam und statisch.
4. **Archivo für Headlines, Inter für alles andere.** Normalschreibung, keine Kursiv-Versalien.
5. **Pill-Buttons, ein Primär-CTA pro Bildschirm.** Sekundäres ist ein Outline-Pill oder ein Text-Link mit Pfeil.
6. **Produkte stehen immer auf einer dunklen Bildbühne,** auch in hellen Sections.
7. **Weißraum vor Inhalt.** Section-Abstand 56–120 px, Text maximal `65ch` breit.
8. **Mobile First:** 16 px Rand, 48 px Touch-Targets, 1–2 Spalten, Sticky-ATC auf der Produktseite.
9. **Bewegung ist Antwort, nicht Show.** Nur Hover-, Fokus- und Reveal-Bewegung, keine Endlos-Loops, `prefers-reduced-motion` respektieren.
10. **Ehrlich:** Platzhalter klar kennzeichnen. Keine erfundenen Bewertungen, Labels, Rabatte oder Claims.

---

## 1. Designprinzipien

| Prinzip | Bedeutung | Prüffrage |
|---|---|---|
| **Technisch-klar** | Raster, Linien, Zahlen, präzise Sprache. Wie ein gut gemachtes Bordhandbuch. | Kann man jedes Element einem Raster und einem Token zuordnen? |
| **Automotiv** | Formensprache aus dem Innenraum: Lichtleisten, Displays, Nachtfahrt. Kein Rennsport-Pathos. | Wirkt es wie ein Premium-Innenraum oder wie Tuning-Werbung? |
| **Premium durch Reduktion** | Wenige Farben, viel Raum, große ruhige Bilder, saubere Typo-Hierarchie. | Kann noch etwas weg? |
| **Licht als Beweis** | Das Produkt *ist* Licht. Dunkle Bühnen zeigen die Wirkung, helle Flächen erklären die Technik. | Zeigt diese dunkle Fläche Licht oder ist sie nur Stimmung? |
| **Zugänglich & schnell** | WCAG 2.2 AA, Tastatur, Screenreader, LCP < 2,5 s mobil, keine Layout-Shifts. | Funktioniert es ohne Maus, ohne Animation, mit 200 % Zoom? |
| **Ehrlich** | Keine Fake-Verknappung, keine Fake-Streichpreise, keine Fantasie-Siegel. | Ist jede Aussage belegbar? |

**Stimmung:** ruhig · präzise · nächtlich · hochwertig · zugänglich.
**Nicht:** laut · aggressiv · verspielt · Gaming-RGB · Neon-Kitsch.

---

## 2. Farb-Tokens

### 2.1 Bestehende Farbschemata (`config/settings_data.json`)

Jedes Schema setzt dieselben Variablen (`snippets/css-variables.liquid`). Komponenten verwenden **nur Variablen**, nie Hex-Werte.

| Variable | `scheme-1` **Hell** (Basis) | `scheme-2` **Fläche** | `scheme-3` **Nachtbühne** |
|---|---|---|---|
| `--color-bg` | `#FFFFFF` | `#F4F6F8` | `#0B0F14` |
| `--color-surface` | `#F4F6F8` | `#FFFFFF` | `#151B23` |
| `--color-text` | `#0B0F14` | `#0B0F14` | `#F2F4F7` |
| `--color-text-muted` | `#4D5866` | `#4D5866` | `#A3ADBA` |
| `--color-accent` | `#006F86` | `#006F86` | `#3DD5EE` |
| `--color-button` | `#0B0F14` | `#0B0F14` | `#3DD5EE` |
| `--color-button-label` | `#FFFFFF` | `#FFFFFF` | `#0B0F14` |
| `--color-border` | `#DDE2E8` | `#DDE2E8` | `#2A3441` |
| `--color-border-strong` | `#8A94A3` | `#8A94A3` | `#6B7685` |
| `--color-sale` | `#B42318` | `#B42318` | `#FF8A7A` |
| `--color-success` | `#157347` | `#157347` | `#4ADE80` |

### 2.2 Geprüfte Kontraste (WCAG 2.2)

| Kombination | Kontrast | Freigabe |
|---|---|---|
| Text `#0B0F14` auf `#FFFFFF` | 19,2 : 1 | ✅ alles |
| Muted `#4D5866` auf `#FFFFFF` / `#F4F6F8` | 7,2 / 6,7 : 1 | ✅ alles |
| Akzent `#006F86` auf `#FFFFFF` / `#F4F6F8` | 5,8 / 5,4 : 1 | ✅ Text ab 14 px, Links, Icons |
| Weiß auf `#006F86` | 5,8 : 1 | ✅ (falls je ein Cyan-Button auf hell nötig ist) |
| Text `#F2F4F7` auf `#0B0F14` | 17,4 : 1 | ✅ alles |
| Muted `#A3ADBA` auf `#0B0F14` / `#151B23` | 8,5 / 7,6 : 1 | ✅ alles |
| Akzent `#3DD5EE` auf `#0B0F14` / `#151B23` | 10,9 / 9,9 : 1 | ✅ alles |
| Label `#0B0F14` auf Button `#3DD5EE` | 10,9 : 1 | ✅ |
| `#8A94A3` (border-strong) auf Weiß | 3,1 : 1 | ⚠️ **nur** für Formular-Rahmen und UI-Grenzen (≥ 3 : 1), **nie für Text** |
| `#6B7685` (border-strong dunkel) auf `#0B0F14` | 4,2 : 1 | ⚠️ nur für UI-Grenzen, nicht für Fließtext |
| `--color-border` hell/dunkel | 1,3 / 1,5 : 1 | Deko-Linie, nie als einzige Grenze eines Bedienelements |

### 2.3 Einsatzregeln

- **Akzent-Budget:** Cyan nimmt höchstens ca. 5 % der sichtbaren Fläche ein. Erlaubt sind Links, Eyebrows/Kapitelmarken, Fokusring, Lichtlinie, aktiver Nav-Zustand, Primär-Button **nur auf dunkel**, Icons in Feature-Listen, Fortschrittsbalken.
- **Primär-Button auf hell ist Nachtblau `#0B0F14`, nicht Cyan.** Das hält helle Seiten ruhig, und der Cyan-Button bleibt der Nachtbühne vorbehalten.
- **Hervorhebungswort in Headlines:** Auf dunkel darf **ein** Wort oder Satzteil in `--color-accent` stehen (`<em class="hero__highlight">`, existiert bereits). Auf hell nur, wenn es die einzige Akzentstelle im Viewport ist.
- **Sale/Rot:** `--color-sale` nur für echte Preisreduzierungen und Fehlermeldungen, nie als Deko.
- **Keine neuen Farben** in Komponenten. Wenn etwas fehlt, wird ein Token oder Schema-Feld ergänzt (Freigabe nötig).
- **Verläufe:** nur `--gradient-bg` aus dem Schema (Theme-Editor) und der radiale `.glow`. Keine Farbverläufe auf Buttons, Text oder Karten.

### 2.4 Glow & Licht (nur auf `scheme-3`)

| Effekt | Umsetzung | Regel |
|---|---|---|
| **Section-Glow** | bestehende Utility `.glow` (radial, 12 % Akzent, oben mittig) | max. 1 pro Nachtbühne, statisch |
| **Lichtlinie** *(umgesetzt: `.light-line`, `.light-edge`, Snippet `light-line`)* | 1 px Linie `linear-gradient(90deg, transparent, var(--color-accent), transparent)` | Signatur-Element: Section-Trenner auf dunkel, Oberkante der Karte bei Hover, aktive Nav. Erinnert an LED-Leisten. |
| **Button-Halo** *(Vorschlag)* | `box-shadow: 0 0 0 4px color-mix(in srgb, var(--color-accent) 22%, transparent)` bei Hover/Fokus | nur Cyan-Button auf dunkel, kein weicher 40-px-Schlagschatten |
| **Bild-Glow** | entsteht **im Foto** (echtes Ambientelicht) | Keine CSS-Glows über Produktbildern |

---

## 3. Typografie-Tokens

### 3.1 Schriften (Theme-Settings, bereits gesetzt)

| Rolle | Setting | Wert | Gewichte |
|---|---|---|---|
| Headlines | `type_heading_font` | **Archivo** `archivo_n6` | 600 (ggf. 700 über `font_modify`, nur nach Freigabe) |
| UI / Fließtext | `type_body_font` | **Inter** `inter_n4` | 400, 600 |
| Headline-Schreibung | `type_heading_case` | `none` | Versalien nur für `.eyebrow` |

Schriften kommen ausschließlich über `font_picker` und `font_face` aus dem Shopify-CDN. Es gibt kein Google-Fonts-`<link>` und keine zusätzlichen Schnitte (Performance).

### 3.2 Skala (`css-variables.liquid`, fluid)

| Token | Mobile (390) | Desktop (1440) | Zeilenhöhe | Laufweite | Einsatz |
|---|---|---|---|---|---|
| `--fs-display` / `.h-display` | 36 px | 80 px | 1,05 | −0,025 em | nur Hero-H1 |
| `--fs-h1` / `h1` | 32 px | 56 px | 1,1 | −0,02 em | Seiten-H1 (Kollektion, Produkt, Seite) |
| `--fs-h2` / `h2` | 28 px | 44 px | 1,15 | −0,015 em | Section-Headline |
| `--fs-h3` / `h3` | 20 px | 24 px | 1,25 | −0,015 em | Karten-, Schritt- und FAQ-Titel |
| `--fs-h4` / `h4` | 17 px | 17 px | 1,35 | 0 | Footer-Spalten, kleine Titel |
| `--fs-lead` / `.lead` | 18 px | 21 px | 1,5 | 0 | Intro unter Headlines |
| `--fs-body` | 16 px | 17 px (≥ 990 px) | 1,6 | 0 | Fließtext |
| `--fs-small` / `.text-small` | 14 px | 14 px | 1,5 | 0 | Meta, Hinweise, Badges |
| `.eyebrow` | 14 px | 14 px | 1,4 | **0,08 em**, VERSALIEN, 600 | Kicker über Headlines |

### 3.3 Regeln

- **Hierarchie pro Section:** Eyebrow (optional) → H2 → Lead (optional) → Inhalt. Genau **eine** H1 pro Seite.
- **Größenverhältnis:** Display ≈ 5 × Body, H2 ≈ 2,75 × Body. Bewusst ruhiger als bei hydrozz (≈ 9 ×).
- **Eyebrows nie unter 14 px** und nie über 0,12 em Laufweite (Lesbarkeit; anders als hydrozz).
- **Kapitelmarke** *(Vorschlag, für Schritte, Einbau-Anleitungen, Ratgeber)*: `<p class="eyebrow chapter"><span class="chapter__index">01</span> Vorbereitung</p>`, Index in `--color-accent`, `font-variant-numeric: tabular-nums`, getrennt durch Abstand statt Gedankenstrich.
- **Zahlen & technische Daten** (Länge, Volt, Farben): Inter mit `font-variant-numeric: tabular-nums`, Einheit mit schmalem Leerzeichen (`5 m`, `12 V`).
- **Silbentrennung:** `hyphens: auto` ist für Headlines aktiv, `lang` am `<html>` muss stimmen. Produktnamen in Karten werden in Inter 600 gesetzt (`.product-card__title`), nicht in Archivo-Versalien.
- **Textbreite:** Fließtext in `.measure` / `.rte` (65 ch). Headlines dürfen breiter laufen, werden mit `text-wrap: balance` gesetzt.
- **Kein** Kursiv für Headlines, **keine** Versalien-Headlines, **kein** Outline-/Verlaufs-Text.

---

## 4. Spacing-, Layout- und Form-Tokens

### 4.1 Abstände (4-px-Raster, bestehend)

| Token | Wert | Typischer Einsatz |
|---|---|---|
| `--space-1` | 4 px | Icon ↔ Label eng |
| `--space-2` | 8 px | Badge-Gruppen, Feld ↔ Label |
| `--space-3` | 12 px | Karteninnenabstand mobil, Liste |
| `--space-4` | 16 px | Standard-Stack, Kartenpadding |
| `--space-5` | 24 px | Headline ↔ Lead, Kartenpadding Desktop |
| `--space-6` | 32 px | Section-Kopf ↔ Inhalt (mobil) |
| `--space-7` | 48 px | Section-Kopf ↔ Inhalt (Desktop), Pagination |
| `--space-8` | 64 px | große Blöcke innerhalb einer Section |
| `--space-9` / `--space-10` | 96 / 128 px | nur Hero und Sonderfälle |

### 4.2 Layout

| Token | Wert | Hinweis |
|---|---|---|
| `--page-width` | 80 rem (1280 px) / Setting 90 rem | Standard-Container `.page-width` |
| `--page-width-wide` | 90 rem | `.page-width--wide` für Grids mit 4 oder mehr Spalten |
| `.page-width--narrow` | 48 rem | FAQ, Rechtstexte, CTA-Banner |
| `--gutter` | 16 → 40 px fluid | Seitenrand; mobil **16 px** (hydrozz: 20 px) |
| `--gap` | 12 → 24 px fluid | Grid-Abstand |
| `--section-y` | 56 → 120 px (normal) / 40 → 80 px (compact) | vertikales Section-Padding über `.section` |
| `--header-height` | 64 px / 76 px ab 990 px | `scroll-padding-top` |

**Breakpoints (bestehend):** `750px` (Tablet), `990px` (Desktop). Weitere nur über Container-Queries (`.cq`), keine zusätzlichen Media-Breakpoints.

**Grid (`.grid` mit `--cols-mobile/tablet/desktop`):**

| Inhalt | Mobile | Tablet | Desktop |
|---|---|---|---|
| Produktkarten | 2 (ab 360 px), sonst 1 | 3 | 4 |
| Kollektionskacheln | 1 (oder 2 bei Quadrat) | 2 | 3 |
| Benefits / USPs | 1 | 2 | 4 |
| Trust-Kacheln | 2 | 2 | 4 |
| Schritte (How-it-works) | 1 | 1 | 3 |
| Blog-Karten | 1 | 2 | 3 |

**Section-Kopf:** Eyebrow + H2 links, „Alle ansehen →“ (`.button--link`) rechts auf der Grundlinie. Mobil steht der Link unter der Headline oder unter dem Grid. Zentrierte Köpfe nur für CTA-Banner, Newsletter und FAQ.

### 4.3 Form

| Token | Wert | Einsatz |
|---|---|---|
| `--radius-s` | 6 px | Inputs, Badges, kleine Flächen |
| `--radius-m` | 12 px | **Karten, Medien, Kacheln** (Standard) |
| `--radius-l` | 20 px | große Feature-Flächen, Drawer-Ecken |
| `--radius-button` | 999 px (Setting „pill“) | alle Buttons, Pagination, Chips |
| `--border-width` | 1 px | Linien |
| `--touch-target` | 48 px | Mindesthöhe und -breite aller Bedienelemente |
| `--shadow-overlay` | `0 8px 32px rgb(11 15 20 / .12)` | nur Overlays (Drawer, Dropdown) |

**Schatten:** Karten haben **keinen** Schatten. Tiefe entsteht durch Fläche (`--color-surface`) oder Linie (`--color-border`). Schatten bleibt Overlays vorbehalten.

---

## 5. Buttons

| Variante | Klasse | Hell (`scheme-1/2`) | Dunkel (`scheme-3`) | Einsatz |
|---|---|---|---|---|
| **Primär** | `.button` | Nachtblau-Pill, weißes Label | **Cyan-Pill**, nachtblaues Label | 1 × pro Viewport: Kaufen, Hauptaktion |
| **Sekundär** | `.button.button--secondary` | Outline in Textfarbe | Outline hell | Alternative Aktion neben Primär |
| **Text-Link** | `.button.button--link` + Pfeil-Icon | Textfarbe, Pfeil bewegt sich 4 px | dito | „Alle ansehen“, „Mehr erfahren“ |
| **Groß** | `+ .button--large` (56 px) | Hero, Buybox, Final CTA | | |
| **Vollbreite** | `+ .button--full` | Buybox, Drawer, mobile Karten | | |
| **Icon** | `.icon-button` (48 × 48) | Header, Stepper, Schließen | | |

**Regeln**
- Mindesthöhe 48 px (`--touch-target`), Label in Inter 600, 16 px, **Normalschreibung** (keine Versalien mit weiter Laufweite).
- Labels sind Verben in der Du-Form: „In den Warenkorb“, „Sets ansehen“, „Kompatibilität prüfen“.
- Hover: Farbmischung (bestehend, 82 %), `:active` mit `scale(.98)`. **Kein** Anheben über 1 px, **kein** Glow-Schatten auf hell.
- Auf dunkel *(Vorschlag)*: zusätzlicher Halo-Ring bei Hover/Fokus (siehe 2.4).
- Zustände Pflicht: `:focus-visible` (2 px Akzent-Outline, bestehend), `disabled`/`aria-disabled`, `aria-busy` (Spinner, bestehend).
- Nie zwei Primär-Buttons nebeneinander. Primär steht links bzw. oben, Sekundär rechts bzw. unten.
- Express-Checkout-Buttons (PayPal, Shop Pay, Klarna) kommen von Shopify (`{{ form | payment_button }}`). Ihre Farben werden **nicht** überschrieben, sie stehen **unter** dem Primär-Button, getrennt durch `--space-3`.

---

## 6. Karten

### 6.1 Produktkarte (`snippets/product-card.liquid`)

```
┌──────────────────────┐
│ [Badge]              │  ← .product-card__badges (max. 2: Sale, Ausverkauft, Neu*)
│                      │
│   PRODUKT auf        │  ← .media.media--stage (dunkle Bühne)
│   DUNKLER BÜHNE      │     Seitenverhältnis 1:1 (Setting image_ratio)
│                      │
└──────────────────────┘
  Lichtset Ambiente 64   ← .product-card__title (Inter 600, 16 px, max. 2 Zeilen)
  64 Farben · 5 m        ← .product-card__variants (muted, 14 px, 1 Zeile, optional)
  ab 49,90 €  59,90 €    ← snippets/price (Preis 600, Vergleichspreis muted + durchgestrichen)
  [ In den Warenkorb ]   ← .product-card__actions (secondary, full, optional)
```

- **Bildbühne immer dunkel**, auch in hellen Sections. Das ist die zentrale Anpassung an hydrozz. Umgesetzt als Modifier `.media--stage` (Token `--color-stage`, siehe §12.3) plus einem dezenten radialen Cyan-Schimmer von unten. Das Produktbild sitzt mit `--fit: contain` und Padding (bestehend 6 %) darin. Lifestyle-Bilder nutzen `cover` ohne Padding.
- Ganze Karte klickbar (bestehend: `.product-card__link::after`). Der Quick-Add-Button liegt mit `z-index: 2` darüber.
- **Hover (nur `@media (hover: hover)`):** Das Bild skaliert auf 1.03 (600 ms, `--ease-out`). Das Zweitbild wird eingeblendet, falls vorhanden (bestehend). Auf dunkel erscheint zusätzlich die Lichtlinie an der Oberkante (`.light-edge`). Kein Anheben, kein Schatten.
- **Inhalt mobil reduzieren:** Kurzbeschreibung entfällt. Der Button bleibt nur, wenn `show_quick_add` aktiv ist, und wird mobil vollbreit unter den Preis gesetzt.
- Badges: `.badge--sale` nur bei echtem `compare_at_price`, `.badge--muted` für „Ausverkauft“, „Neu“ nur mit Datumslogik bzw. Tag (nicht erfinden).
- Karten **ohne** Rahmen und Schatten auf hell. Auf dunkel bekommt die Bildfläche einen 1-px-Rahmen in `--color-border`, damit die Bühne sich vom Hintergrund löst.

### 6.2 Inhaltskarten (Benefits, Schritte, Blog, Kollektionen)

- Fläche `--color-surface`, Radius `--radius-m`, Padding `--space-5` (mobil `--space-4`), keine Schatten.
- Icon (24 px, `--color-accent`) → H3 → 1–2 Sätze muted. Keine Icon-Kreise, keine bunten Hintergründe.
- **Kollektionskachel:** Bild 3 : 2 oder 4 : 5 mit Titel darunter (nicht auf dem Bild). Auf dunkel ist Text-auf-Bild erlaubt, dann mit Verlauf `linear-gradient(to top, rgb(11 15 20 / .85), transparent 60%)`.
- **Trust-Kachel** (wie `sections/trust-bar.liquid`): Icon oder kurze Akzentlinie, Titel (Inter 600) und eine Zeile muted. Keine Payment-Logo-Wand außer im Footer und unter dem Buybox-CTA (dynamisch über `shop.enabled_payment_types`).

---

## 7. Bildregeln

### 7.1 Motive

| Typ | Motiv | Bühne | Format |
|---|---|---|---|
| **Produkt (Packshot)** | Lichtset / LED-Streifen **leuchtend**, Kabel ordentlich, Lieferumfang | dunkler Hintergrund `#0B0F14`–`#151B23`, weiches Streiflicht, gleiche Perspektive je Serie | 1 : 1 (Karte, Galerie), 2048 px |
| **Produkt (Detail)** | Stecker, Controller, Klebeband, Lichtleiter-Querschnitt | dunkel oder neutralgrau | 1 : 1 |
| **Szene (Hero / Nachtbühne)** | Fahrzeuginnenraum bei Nacht, Licht in Türleisten/Fußraum/Armaturenbrett, Blaue Stunde | real dunkel, Licht als einzige Farbquelle | 16 : 9 Desktop, **4 : 5 mobil** (`image_mobile`) |
| **Vorher/Nachher** *(Vorschlag)* | gleicher Innenraum ohne / mit Ambientelicht, identische Kameraposition | dunkel | 16 : 9 / 4 : 5 |
| **Anleitung** | Hände beim Einbau, Verlegen, Clip setzen | hell, sachlich, gute Ausleuchtung | 3 : 2 |
| **Ratgeber** | Farbtemperatur-Vergleich, Kompatibilitätsdetails | hell oder dunkel je Thema | 3 : 2 |

### 7.2 Regeln

- **Keine Freisteller auf Weiß.** Produkte stehen immer auf der dunklen Bühne, damit das Licht wirkt.
- **Licht muss echt sein:** keine nachträglich aufgemalten Glows oder RGB-Regenbögen. Farbe nach Möglichkeit Cyan/Eisblau oder warmweiß, damit sie zur Marke passt. Weitere Farben nur, wenn die Variante es verlangt.
- **Keine Texte im Bild** (SEO, Barrierefreiheit, Übersetzung). Headlines stehen als HTML darüber oder daneben.
- **Fremde Fahrzeugmarken:** Logos und Embleme nicht prominent zeigen bzw. retuschieren (Markenrecht).
- **Overlays:** Text auf Bild nur in Nachtbühnen, mit `.hero__overlay`-Verlauf (Setting `overlay_opacity`). Mobil steht der Text **unter** dem Bild, sofern das Motiv keinen ruhigen Bereich hat (gelerntes hydrozz-Muster).
- **Weißraum:** Auf hellen Sections hält das Bild zum Text mindestens `--space-7` Abstand. Bilder füllen ihr Raster, schwimmen aber nie randlos zwischen Text.
- **Technik:** Immer über `snippets/image.liquid` bzw. `image_url` und `image_tag` mit `widths` und `sizes`. Der Hero bekommt `loading: 'eager'` und `fetchpriority: 'high'`, alle anderen `lazy`. `alt` kommt aus dem Admin, bei Deko leer. Videos laufen stumm, mit Poster, `playsinline`, ohne Autoplay bei `prefers-reduced-motion`.
- **Platzhalter:** Bis echte Bilder vorliegen: `placeholder_svg_tag` auf `--color-surface` plus `.badge--muted`-Label „PLATZHALTER“ (bestehendes Muster im Hero).

---

## 8. Section-Rhythmus

### 8.1 Startseite (aktuelle `templates/index.json`, bewertet)

| # | Section | Schema | Rolle | Bewertung |
|---|---|---|---|---|
| 1 | `hero` | **3 Nacht** | Emotion + 1 CTA | ✅ |
| 2 | `trust-bar` | 2 Fläche | Risikoabbau direkt unter dem Hero | ✅ |
| 3 | `featured-collection` (Bestseller) | 1 Hell | kaufbar, früh | ⚠️ Karten noch **ohne** `stage: true` (offen, siehe §13) |
| 4 | `benefits` | 1 Hell | Rationalisierung | ✅ |
| 5 | `how-it-works` | **3 Nacht** | Einbau in 3 Schritten | ✅ |
| 6 | `image-with-text` (Story) | **3 Nacht** | Stimmung / Marke | ⚠️ zwei Nachtbühnen in Folge, mit Lichtlinie trennen oder Story auf hell stellen |
| 7 | `social-proof` | 1 Hell | – | ⚠️ ausblenden, bis echte Inhalte existieren |
| 8 | `collection-list` | 1 Hell | Orientierung | ✅ |
| 9 | `faq` | 2 Fläche | Einwände | ✅ |
| 10 | `blog-posts` | 1 Hell | SEO / Kompetenz | ✅ |
| 11 | `newsletter` | 1 Hell | Bindung | ✅ (Shopify-Kundenformular) |
| 12 | `cta-banner` | **3 Nacht** + `.glow` | Abschluss | ✅ |

**Optional (Freigabe nötig):** Eine Vorher/Nachher-Nachtbühne „ohne / mit Licht“ nach den Bestsellern ist der stärkste visuelle Beweis.

### 8.2 Regeln

- **Wechsel hell ↔ dunkel** strukturiert die Seite. Zwei gleichfarbige helle Sections hintereinander sind ok (Trennung durch Weißraum), zwei Nachtbühnen nur, wenn sie inhaltlich eine Einheit bilden.
- **`scheme-1` → `scheme-2`** ist ein weicher Wechsel für Info-Blöcke (Trust, FAQ). **`scheme-3`** ist ein harter Wechsel für Inszenierung.
- Abfolge **Emotion → Beweis → Produkt → Erklärung → Einwand → Abschluss.** Kaufbare Produkte erscheinen spätestens im 3. Bildschirm.
- Jede Section hat **ein** Thema, **eine** Headline und höchstens **einen** CTA.
- Abstände kommen nur über `.section` (`--section-y`). Keine Section setzt eigenes vertikales Padding, außer Hero und Trust-Bar (kompakt).
- **Ausnahme Template-Seiten** (Kollektion, Produkt, Seite, Artikel), die mit einer Breadcrumb beginnen: oben nur `--space-5` (mobil) bzw. `--space-6` (ab 990 px), damit Breadcrumb und H1 nah am Header stehen. Unten gilt weiter `--section-y`.
- Header (`scheme-1`) und Announcement-Bar (`scheme-3`) bleiben, der Footer ist `scheme-3`. Damit endet jede Seite auf einer Nachtbühne.

### 8.3 Weitere Seiten

| Seite | Rhythmus |
|---|---|
| **Kollektion** *(umgesetzt, Schritt 7)* | Hell: Breadcrumb → H1 + Beschreibung → Toolbar (Filter-Button mobil, Anzahl, Sortierung) → aktive Filter-Chips → Sidebar-Filter (ab 990 px) bzw. Drawer (mobil) + Grid 2/3/4 auf `.media--stage` → Pagination → SEO-Text (Metafeld `custom.seo_text` oder Section-Setting, nur Seite 1 ohne Filter). Steuerhinweis pro Karte, Versandkosten-Link im Footer. Ohne JS: Filter inline über dem Grid. |
| **Produkt** | Hell: Galerie (dunkle Bühne) + Buybox → Nutzen-Liste → Lieferumfang/Technik (Tabelle) → Kompatibilität (`custom.kompatibilitaet`) → **Nachtbühne** „So wirkt es“ → Einbau-Schritte → FAQ → verwandte Produkte. |
| **Warenkorb** | Hell, ruhig: Positionen → Fortschritt Gratisversand → Summe → Primär-CTA „Zur Kasse“ → Express-Buttons → Hinweis Widerruf/Versand. **Keine** Nachtbühne, kein Cross-Sell-Lärm. |
| **Ratgeber / Artikel** | Hell, `.page-width--narrow`, `.rte`, Kapitelmarken, Bilder 3 : 2. |

---

## 9. Mobile-Regeln

| Bereich | Regel |
|---|---|
| **Raster** | 16 px Seitenrand (`--gutter`), 1–2 Spalten, kein horizontales Scrollen der Seite (Karussells nur mit `scroll-snap`, sichtbarem Anschnitt und Tastaturbedienung). |
| **Touch** | Alle Bedienelemente mindestens **48 × 48 px** (`--touch-target`), auch Header-Icons, Stepper, Filter-Chips, Akkordeons. Abstand zwischen Targets ≥ 8 px. |
| **Header** | 64 px, Sticky (Setting). Burger links, Logo, Warenkorb rechts mit Zähler. Suche im Menü-Drawer oder als Icon. Optional: beim Runterscrollen ausblenden, beim Hochscrollen einblenden (nur ohne Reduced Motion). |
| **Menü-Drawer** | **Vollständig deckender Hintergrund** (`--color-bg` des Schemas, kein Blur, keine Transparenz). Links 48 px hoch, Fokus-Falle, `Esc` schließt, Scroll-Lock (bestehend `data-scroll-lock`). |
| **Hero** | Mobiles Bild über `image_mobile` (4 : 5). Text unter oder über dem Bild nur mit ausreichendem Overlay. H1 nicht größer als 36–40 px, ein Primär-CTA vollbreit oder ≥ 56 px hoch. Höhe max. `100svh` minus Header. |
| **Produktkarten** | 2 Spalten ab 360 px. Titel max. 2 Zeilen (`line-clamp`), Preis immer sichtbar, Button optional und vollbreit. |
| **Produktseite** | Galerie als Swipe mit Zähler („1 / 5“) statt Punkten. Buybox direkt darunter. **Sticky-ATC-Leiste** unten, sobald der Haupt-Button aus dem Viewport ist (IntersectionObserver), mit `safe-area-inset-bottom`. |
| **Typo** | Body 16 px, Inputs ≥ 16 px (kein iOS-Zoom), Eyebrow 14 px. |
| **Footer** | Menüspalten als `<details>`-Akkordeons (≤ 749 px), Rechtliches und Zahlarten immer sichtbar. |
| **Performance** | LCP-Bild ≤ 200 KB mobil, keine Autoplay-Videos über 2 MB, JS nur in betroffenen Sections (`{% javascript %}`), keine Drittanbieter-Skripte ohne Freigabe. |

---

## 10. Motion

| Token | Wert | Einsatz |
|---|---|---|
| `--duration-fast` | 150 ms | Farbe, Rahmen, Button-Press |
| `--duration-base` | 250 ms | Pfeil-Shift, Einblenden Zweitbild, Drawer-Overlay |
| `--duration-slow` | 600 ms | Bild-Zoom, Reveal |
| `--ease-out` | `cubic-bezier(.2,.7,.2,1)` | Standard für alles |

- **Erlaubt:** Hover/Fokus-Feedback, Bild-Zoom auf 1.03, Pfeil-Shift 4 px, Drawer-Slide (250 ms), Scroll-Reveal (bestehend `.reveal` über `animation-timeline: view()`, nur wenn `settings.animations_enabled`), Akkordeon-Höhe.
- **Verboten:** Endlos-Animationen (laufende Verläufe, Marquee-Bars, pulsierende Glows), Bounce/Spring-Easing, Parallax, Autoplay-Karussells, Scroll-Hijacking, Cursor-Effekte, RGB-Farbwechsel-Animationen.
- **Reveal:** nur ganze Blöcke (Section-Kopf, Grid-Elemente), nie einzelne Wörter. Versatz maximal 24 px. Inhalte sind ohne Animation sofort sichtbar (Progressive Enhancement).
- **Video:** nur in Nachtbühnen (Hero, Vorher/Nachher). Stumm, Loop ≤ 15 s, mit Poster und Pause-Button. Bei `prefers-reduced-motion` wird das Poster statt Autoplay gezeigt.
- `prefers-reduced-motion: reduce` deaktiviert global alle Transitions und Animationen (bestehend in `critical.css` §14).

---

## 11. Do's and Don'ts

| ✅ Do | ❌ Don't |
|---|---|
| Hell als Basis, dunkle Nachtbühnen gezielt für Licht-Inszenierung | Komplette Seite dunkel (hydrozz-Stil) |
| Ein Akzent (Cyan), schema-abhängig `#006F86` / `#3DD5EE` | Zweite Akzentfarbe, Rot als Deko, RGB-Regenbogen |
| Archivo 600 in Normalschreibung, Inter für UI | Kursiv-Versalien-Headlines, Outline-Text, Metallic-Verlauf |
| Produkte auf dunkler Bildbühne | Freisteller auf Weiß, Text im Bild |
| Pill-Buttons, ein Primär-CTA pro Viewport | Glow-Schatten auf jedem Button, Versalien-Labels mit 0,2 em Laufweite |
| Eyebrow 14 px / 0,08 em | Eyebrow 11 px / 0,4 em |
| 48-px-Targets überall | Icons mit 22 px Trefferfläche |
| Deckender Menü-Drawer | Transparente Overlays über Inhalt |
| Lichtlinie / `.glow` nur auf dunkel, statisch | Laufende Verläufe, pulsierendes Licht |
| Variablen und Schemata | Hex-Werte in Sections, Inline-Styles außer CSS-Variablen |
| Echte Preise, echte Rabatte, echte Bewertungen | „−33 %“ ohne Referenzpreis, erfundene Bestseller-Labels, Countdown-Timer |
| Payment-Icons dynamisch (`shop.enabled_payment_types`) | Hart codierte Zahlungslogos |
| Theme-eigene Komponenten für Drawer und Upsell | App-Widgets im Fremdstil ohne Anpassung |
| Einheitliche Container (`.page-width`) | Unterschiedliche Breiten zwischen Sections und Footer |
| `hyphens: auto`, `text-wrap: balance` | Wortbruch mitten im Wort in schmalen Karten |

---

## 12. Umsetzungshinweise für das Skeleton Theme

> Die folgenden Snippets sind **Vorlagen** für spätere, einzeln freigegebene Schritte. In diesem Schritt wird **keine Theme-Datei** geändert.

### 12.1 Architektur

- **Tokens:** ausschließlich in `snippets/css-variables.liquid` (aus Settings) und `:root`. Neue Tokens zuerst dort, nie lokal in Sections erfinden.
- **Globale Utilities:** `assets/critical.css` (Reset, Typo, Buttons, Grid, Media, Badges, Motion). Neue Utilities wie `.light-line`, `.media--stage` oder `.chapter` gehören hierher, weil sie seitenübergreifend sind.
- **Komponenten-CSS:** im `{% stylesheet %}` der jeweiligen Section bzw. des Snippets. BEM-Klassen nach Muster `section-name__element--modifier`.
- **Farben pro Section:** immer das Setting `color_scheme` (Typ `color_scheme`) plus die Klasse `color-{{ section.settings.color_scheme }}` am Wurzelelement. Komponenten erben die Variablen automatisch.
- **Einzelwerte aus Settings:** als CSS-Variable inline (`style="--ratio: {{ … }}"`). Mehrere Eigenschaften steuert man über Modifier-Klassen (siehe AGENTS.md).
- **Texte:** alle UI-Strings in `locales/de.default.json` (`{{ 'key' | t }}`), Editor-Labels in `locales/de.schema.json` / `en.default.schema.json`.

### 12.2 Section-Grundgerüst

```liquid
<section
  class="feature section color-{{ section.settings.color_scheme }}{% if section.settings.glow %} glow{% endif %}"
  aria-labelledby="Heading-{{ section.id }}"
>
  <div class="page-width">
    {%- assign heading_id = 'Heading-' | append: section.id -%}
    {% render 'section-heading',
      eyebrow: section.settings.eyebrow,
      heading: section.settings.heading,
      id: heading_id,
      link_label: section.settings.link_label,
      link_url: section.settings.link_url
    %}
    <div class="grid" style="--cols-mobile: 1; --cols-tablet: 2; --cols-desktop: {{ section.settings.columns_desktop }};">
      {%- for block in section.blocks -%}
        <div class="reveal" {{ block.shopify_attributes }}>…</div>
      {%- endfor -%}
    </div>
  </div>
</section>

{% schema %}
{
  "name": "t:sections.feature.name",
  "settings": [
    { "type": "color_scheme", "id": "color_scheme", "label": "t:settings.color_scheme", "default": "scheme-1" },
    { "type": "checkbox", "id": "glow", "label": "t:settings.glow", "default": false }
  ]
}
{% endschema %}
```

*(Parameter laut `{% doc %}` von `snippets/section-heading.liquid`: `eyebrow`, `heading`, `text`, `link_label`, `link_url`, `align`, `id`. Locale-Keys `t:settings.color_scheme` und `t:settings.glow` existieren bereits in `de.schema.json`.)*

### 12.3 Bühne & Licht – umgesetzt (Vorbereitung Schritt 7)

**Tokens** in `snippets/css-variables.liquid` (`:root`, schema-unabhängig, entsprechen den Nacht-Defaults):

| Token | Wert | Zweck |
|---|---|---|
| `--color-stage` | `#0B0F14` | Hintergrund der Produktbildbühne |
| `--color-stage-edge` | `#2A3441` | Rahmen der Bühne in dunklen Sections |
| `--color-stage-text` | `#F2F4F7` | Inhalt auf der Bühne (Platzhalter-Illustration) |
| `--color-stage-glow` | `#3DD5EE` | Lichtschimmer der Bühne, unabhängig vom hellen Akzent |
| `--color-backdrop` | `rgb(11 15 20 / .55)` | Dimmung hinter modalen Drawern (`::backdrop`); auf `:root, ::backdrop` gesetzt, weil `::backdrop` nicht überall erbt (Schritt 7) |

**Klassen** in `assets/critical.css`:

| Klasse | Abschnitt | Wirkung |
|---|---|---|
| `.media--stage` | 9. Media | dunkle Bühne + radialer Cyan-Schimmer von unten; in `.color-scheme-3` zusätzlich 1-px-Rahmen; Platzhalter-SVG hell auf dunkel |
| `.light-line` | 12. Utilities | 1-px-Linie, Verlauf transparent → `--color-accent` → transparent, 70 % Deckkraft |
| `.light-edge` | 12. Utilities | Lichtlinie an der Oberkante, erscheint bei `:hover` (nur Hover-Geräte) und `:focus-within` |

**Snippet** `snippets/light-line.liquid`: dekorativ (`<span aria-hidden="true">`) oder mit `separator: true` als semantisches `<hr>`.

**Verwendung**

```liquid
{%- comment -%} Produktbild auf Bühne (Packshot) {%- endcomment -%}
{% render 'image', image: product.featured_image, class: 'media--stage', fit: 'contain', ratio: '1 / 1', sizes: '(min-width: 990px) 25vw, 50vw' %}

{%- comment -%} Lichtlinie in einer Nachtbühne {%- endcomment -%}
{% render 'light-line' %}

{%- comment -%} Karte mit Lichtkante (nur in scheme-3 einsetzen) {%- endcomment -%}
<div class="product-card light-edge">…</div>
```

Regeln: `.light-line` und `.light-edge` nur in `scheme-3`; `.media--stage` in allen Schemata für Produktbilder (nicht für Lifestyle-Bilder). Die Bühne setzt kein `--fit` – `fit: 'contain'` wird beim Rendern übergeben.

### 12.4 Weitere Utilities *(Vorschlag, noch nicht umgesetzt)*

```css
/* Chapter marker for steps and guides */
.chapter__index {
  color: var(--color-accent);
  font-variant-numeric: tabular-nums;
  margin-inline-end: var(--space-2);
}

/* Halo for the cyan primary button on dark schemes */
@media (hover: hover) {
  .color-scheme-3 .button:not(.button--secondary, .button--link):hover {
    box-shadow: 0 0 0 4px color-mix(in srgb, var(--color-accent) 22%, transparent);
  }
}
```

> Hinweis: Die Schema-Klassen heißen `color-scheme-1/2/3` (aus `color-{{ scheme.id }}`). Selektoren auf Schemata sind nur für diese wenigen globalen Licht-Effekte zulässig. Komponenten arbeiten sonst ausschließlich mit Variablen.

### 12.5 Produktkarte mit Bühne

```liquid
<div class="product-card__media">
  <a href="{{ product.url }}" class="media media--stage" style="--ratio: {{ settings_ratio | default: '1 / 1' }};" tabindex="-1" aria-hidden="true">
    {{ product.featured_media | image_url: width: 900 | image_tag:
      widths: '240, 360, 480, 640, 900',
      sizes: '(min-width: 990px) calc((min(100vw, 80rem) - 3 * var(--gap)) / 4), (min-width: 750px) 33vw, 50vw',
      loading: 'lazy',
      alt: product.featured_media.alt | escape
    }}
  </a>
</div>
```

```css
/* {% stylesheet %} in product-card.liquid */
@media (hover: hover) {
  .product-card:hover .media--stage > img { transform: scale(1.03); }
}
.product-card__title {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

### 12.6 Sticky-ATC (Produktseite, mobil)

```liquid
<div class="sticky-atc color-{{ section.settings.color_scheme }}" data-sticky-atc hidden>
  <span class="sticky-atc__title">{{ product.title }}</span>
  {% render 'price', product: product %}
  <button type="submit" form="{{ product_form_id }}" class="button">{{ 'products.add_to_cart' | t }}</button>
</div>

{% javascript %}
  const main = document.querySelector('[data-main-atc]');
  const bar = document.querySelector('[data-sticky-atc]');
  if (main && bar && 'IntersectionObserver' in window) {
    new IntersectionObserver(([entry]) => { bar.hidden = entry.isIntersecting; }).observe(main);
  }
{% endjavascript %}
```

```css
.sticky-atc {
  position: fixed;
  inset-inline: 0;
  inset-block-end: 0;
  z-index: 20;
  display: flex;
  align-items: center;
  gap: var(--space-3);
  padding: var(--space-3) var(--gutter) calc(var(--space-3) + env(safe-area-inset-bottom));
  background: var(--color-bg);
  border-top: var(--border-width) solid var(--color-border);
}
@media (min-width: 990px) { .sticky-atc { display: none; } }
```

### 12.7 Gratisversand-Fortschritt (Warenkorb / Drawer)

```liquid
{%- liquid
  assign threshold = settings.free_shipping_threshold | times: 100
  assign remaining = threshold | minus: cart.total_price
  assign progress = cart.total_price | times: 100 | divided_by: threshold | at_most: 100
  assign remaining_money = remaining | money
-%}
<div class="shipping-progress" style="--progress: {{ progress }}%;">
  <p class="text-small">
    {%- if remaining > 0 -%}
      {{ 'cart.free_shipping_remaining' | t: amount: remaining_money }}
    {%- else -%}
      {{ 'cart.free_shipping_reached' | t }}
    {%- endif -%}
  </p>
  <div class="shipping-progress__bar" role="progressbar" aria-valuemin="0" aria-valuemax="100" aria-valuenow="{{ progress }}"></div>
</div>
```

Die Schwelle kommt aus `settings.free_shipping_threshold` (nur DE, siehe Setting-Hinweis). Der Balken ist in `--color-accent` gefüllt, die Spur in `--color-border`. Die Keys `cart.free_shipping_remaining` und `cart.free_shipping_reached` sind **neu anzulegen** (bisher existieren nur `announcement.free_shipping` und `sections.trust_bar.free_shipping`). Den Betrag vor der Übergabe an `t` mit `| money` formatieren (`assign remaining_money = remaining | money`).

### 12.8 Theme-Settings – Leitplanken

| Setting | Wert laut Design-Sprache |
|---|---|
| `type_heading_font` | `archivo_n6` |
| `type_body_font` | `inter_n4` |
| `type_heading_case` | `none` |
| `button_radius` | `pill` |
| `page_width` | `80rem` (Standard), `90rem` nur für sehr bildlastige Shops |
| `section_spacing` | `normal` |
| `animations_enabled` | `true` (Reveal), wird durch Reduced Motion übersteuert |
| Farbschemata | Werte aus §2.1. Merchant-Änderungen müssen die Kontrastwerte in §2.2 halten. |

### 12.9 Qualitäts-Checkliste je UI-Schritt

- [ ] Nur Tokens und Variablen, keine Hex-Werte, keine neuen Farben
- [ ] `color_scheme`-Setting vorhanden, Section in allen 3 Schemata lesbar
- [ ] Eine H1 pro Seite, Überschriften-Hierarchie lückenlos
- [ ] Buttons: Pill, ≥ 48 px, ein Primär-CTA pro Viewport, Fokus sichtbar
- [ ] Produktbilder auf `.media--stage`, `image_tag` mit `widths` und `sizes`
- [ ] Mobile 390 px: kein horizontaler Scroll, Targets ≥ 48 px, Text ≥ 16 px
- [ ] Motion nur über Tokens, Reduced Motion geprüft
- [ ] Texte über Locales, Platzhalter als „PLATZHALTER“ gekennzeichnet
- [ ] Keine Claims, Bewertungen oder Rabatte ohne echte Daten
- [ ] `shopify theme check` ohne neue Fehler

---

## 13. Offene Punkte (Stand nach Schritt 7)

| Punkt | Bezug | Entscheidung |
|---|---|---|
| Startseiten-Bestseller auf dunkle Bühne (`stage: true` in `sections/featured-collection.liquid` oder Default `true` in `product-card`) | §0 Regel 6, §6.1, §8.1 | Nutzer |
| Header-Backdrop (`sections/header.liquid`) von `rgb(11 15 20 / …)` auf `var(--color-backdrop)` umstellen | §2.3, §12.3 | Folgeaufgabe |
| Paginierung mobil: Umbruch hinnehmen (aktuell) oder kompakt „‹ aktuelle Seite ±1 ›“ | §9 | Nutzer |
| Steuerhinweis pro Karte + Versandkosten-Link nur im Footer rechtlich bestätigen | §6.1 | Nutzer |
| Kapitelmarke `.chapter` und Button-Halo (§12.4) noch nicht umgesetzt | §3.3, §5 | bei Bedarf |
| `snippets/light-line.liquid` noch ungenutzt (Theme-Check-Warnung OrphanedSnippet) | §2.4 | mit erster Nachtbühne nutzen |
