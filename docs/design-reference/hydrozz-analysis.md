# Design-Analyse: hydrozz.de

> **Zweck:** Referenz-Analyse für die Design-Sprache von carbiente ([design-language.md](design-language.md)).
> Wir extrahieren **Prinzipien, Muster und Stimmung** – keine Texte, Bilder, Claims oder Markenelemente.
>
> **Stand:** 2026-10-05 · **Methode:** Playwright (Chromium), Viewports 390×844, 768×1024, 1440×900, berechnete Styles per `getComputedStyle`.
> **Technische Basis von hydrozz:** Shopify, Horizon 3.1 mit stark angepasster Startseite (eigene `hz2_home`-Section, Klassenpräfix `h2-`), Produkt- und Warenkorbseite weitgehend Horizon-Standard plus Apps.
>
> Screenshots liegen in [`hydrozz/`](hydrozz/), insgesamt 58 Dateien. Die Bilder sind Eigentum von hydrozz und dienen nur der internen Referenz. Sie werden nicht veröffentlicht und nicht ins Theme übernommen.

---

## Screenshot-Index

| Bereich | Desktop 1440 | Tablet 768 | Mobile 390 |
|---|---|---|---|
| Startseite – Hero | [home-desktop-hero](hydrozz/home-desktop-hero.png) | [home-tablet-hero](hydrozz/home-tablet-hero.png) | [home-mobile-hero](hydrozz/home-mobile-hero.png) |
| Startseite – komplett | [home-desktop-full](hydrozz/home-desktop-full.png) | [home-tablet-full](hydrozz/home-tablet-full.png) | [home-mobile-full](hydrozz/home-mobile-full.png) |
| Bestseller-Grid | [home-desktop-best](hydrozz/home-desktop-best.png) | – | [home-mobile-best](hydrozz/home-mobile-best.png) |
| Varianten-Kacheln | [home-desktop-flags](hydrozz/home-desktop-flags.png) | – | [home-mobile-flags](hydrozz/home-mobile-flags.png) |
| Vorher/Nachher-Slider | [home-desktop-before-after](hydrozz/home-desktop-before-after.png) | – | [home-mobile-before-after](hydrozz/home-mobile-before-after.png) |
| USP-Spalten | [home-desktop-usp](hydrozz/home-desktop-usp.png) | – | [home-mobile-usp](hydrozz/home-mobile-usp.png) |
| Bundles | [home-desktop-sets](hydrozz/home-desktop-sets.png) | – | [home-mobile-sets](hydrozz/home-mobile-sets.png) |
| UGC / Community | [home-desktop-community](hydrozz/home-desktop-community.png) | – | [home-mobile-community](hydrozz/home-mobile-community.png) |
| Trust-Kacheln | [home-desktop-trust](hydrozz/home-desktop-trust.png) | – | [home-mobile-trust](hydrozz/home-mobile-trust.png) |
| Hover: Karten | [cards-rest](hydrozz/home-desktop-cards-rest.png) / [cards-hover](hydrozz/home-desktop-cards-hover.png) | – | – |
| Hover: Button / Nav | [hero-button-hover](hydrozz/home-desktop-hero-button-hover.png) / [nav-hover](hydrozz/header-desktop-nav-hover.png) | – | – |
| Header | [header-desktop](hydrozz/header-desktop.png) | [header-tablet](hydrozz/header-tablet.png) | [header-mobile](hydrozz/header-mobile.png) |
| Mobile-Menü offen | – | [header-tablet-menu-open](hydrozz/header-tablet-menu-open.png) | [header-mobile-menu-open](hydrozz/header-mobile-menu-open.png) |
| Footer | [footer-desktop](hydrozz/footer-desktop.png) | [footer-tablet](hydrozz/footer-tablet.png) | [footer-mobile](hydrozz/footer-mobile.png) |
| Kollektion | [collection-desktop](hydrozz/collection-desktop.png) · [full](hydrozz/collection-desktop-full.png) | [collection-tablet](hydrozz/collection-tablet.png) · [full](hydrozz/collection-tablet-full.png) | [collection-mobile](hydrozz/collection-mobile.png) · [full](hydrozz/collection-mobile-full.png) |
| Produktseite | [product-desktop](hydrozz/product-desktop.png) · [full](hydrozz/product-desktop-full.png) · [scrolled](hydrozz/product-desktop-scrolled.png) | [product-tablet](hydrozz/product-tablet.png) · [full](hydrozz/product-tablet-full.png) · [scrolled](hydrozz/product-tablet-scrolled.png) | [product-mobile](hydrozz/product-mobile.png) · [full](hydrozz/product-mobile-full.png) · [scrolled](hydrozz/product-mobile-scrolled.png) |
| Warenkorb-Drawer | [cart-desktop-drawer](hydrozz/cart-desktop-drawer.png) | [cart-tablet-drawer](hydrozz/cart-tablet-drawer.png) | [cart-mobile-drawer](hydrozz/cart-mobile-drawer.png) |
| Warenkorb-Seite | [cart-desktop](hydrozz/cart-desktop.png) · [full](hydrozz/cart-desktop-full.png) | [cart-tablet](hydrozz/cart-tablet.png) · [full](hydrozz/cart-tablet-full.png) | [cart-mobile](hydrozz/cart-mobile.png) · [full](hydrozz/cart-mobile-full.png) |
| Pop-up-Prüfung (nach 12 s) | [home-desktop-after-12s](hydrozz/home-desktop-after-12s.png) | – | [home-mobile-after-12s](hydrozz/home-mobile-after-12s.png) |

Der Checkout wurde nicht geöffnet: Er läuft über Shopify und ist für die Design-Sprache nicht relevant.

---

## 1. Gesamteindruck

**Visuelle Positionierung:** Die Seite ist komplett dunkel gestaltet (`#0B0D10` / `#050506`) und setzt einen einzigen Signalakzent in Rot (`#E02A1E` bis `#FF4A3D`). Die Bühne ist eine dunkle Tiefgarage mit Neonröhren und einem Supersportwagen. Das Ergebnis ist eher Motorsport- bzw. Tuning-Ästhetik als Detailing-Labor.

**Markenpersönlichkeit:** laut, selbstbewusst, Community-getrieben, jung. Englische Claims in Versalien und kursiv („Performance“-Anmutung) treffen auf deutsche Erklärtexte.

**Emotionale Wirkung:** Adrenalin und Exklusivität. Die Produkte wirken als Teil eines Lifestyles („Represent your roots“, Community), nicht als bloßes Pflegezubehör.

**Warum es modern und premium wirkt:**
1. **Ein Akzent, konsequent eingesetzt:** Rot erscheint nur auf Eyebrows, Hervorhebungswörtern, CTAs, Badges und Trennlinien. Alles andere ist Graustufe.
2. **Dunkle Bühne für die Produkte:** Jedes Produktfoto ist eine Low-Key-Aufnahme auf schwarzem Lack. Der rote bzw. farbige Artikel leuchtet dadurch förmlich.
3. **Extremer Typo-Kontrast:** 124-px-Display-Headline (Saira 800 italic, Versalien) neben 14–16-px-Fließtext und 11–12-px-Eyebrows mit sehr weiter Laufweite.
4. **Großzügige Sections:** 120 px vertikales Padding auf Desktop, pro Section genau ein Thema.
5. **Dezente Lichteffekte:** radiale Rot-Glows am Section-Kopf, ein diagonaler „Lichtstreifen“ im Hero, Glow-Schatten unter dem Primär-CTA.
6. **Nummerierte Kapitel** („01 — Bestseller“, „02 — …“) suggerieren Editorial/Magazin und Struktur.

**Schwächen (wichtig für uns):** Die Konsistenz bricht ab der Produktseite. Dort und im Warenkorb gelten andere Schriften (Inter statt Saira für H2), andere Radien (14 px statt Pill), andere Rottöne, App-Widgets mit eckigen Buttons, eine weiße Summen-Box auf dunkler Seite und ein gelber PayPal-Button. Die Premium-Wirkung trägt also vor allem die Startseite.

---

## 2. Layout und Raster

| Merkmal | Desktop 1440 | Tablet 768 | Mobile 390 |
|---|---|---|---|
| Content-Breite Startseite | 1296 px (`max-width: 1440px`, `padding: 0 72px`) | 691 px | 351 px |
| Seitenrand (Gutter) | **72 px** (5 %) | 38 px | **20 px** |
| Content-Breite Footer / Kollektion | 1200 px (x = 120) – *inkonsistent zur Startseite* | – | – |
| Produktseite | randlos links (Galerie ab x = 40), Buybox rechts ≈ 430 px | – | – |
| Section-Padding vertikal | **120 px** oben und unten | ≈ 69 px | **64 px** |
| Hero-Höhe | 900 px (= 100 vh) | 920 px | 844 px (= 100 svh) |

**Grids (gemessen):**
- Bestseller: 4 Spalten × 307 px, Gap 22 px → Mobile/Tablet 2 Spalten, Gap 16 px.
- Varianten-Kacheln: 7 Spalten × 173 px, Gap 14 px → Mobile 2 Spalten.
- Bundles: 3 Spalten × 417 px, Gap 22 px.
- UGC-Videos: 5 Spalten, Gap 16 px (Hochformat 9:16).
- Trust: 4 Spalten, Gap 14 px.
- Footer: 4 Spalten (1,4 : 1 : 1 : 1), Gap 36 px → Mobile 1 Spalte.

**Symmetrie:** Section-Köpfe sind **asymmetrisch**: Headline linksbündig, „Alle ansehen →“-Link rechtsbündig auf der Grundlinie. Nur der Footer-CTA ist zentriert. Der Hero ist links ausgerichtet, das Motiv steht rechts (Text-über-Bild mit Verlauf von links).

**Bildschirmhöhen:** Der Hero nutzt 100 % der Bildschirmhöhe. Die übrigen Sections sind inhaltshoch. Der Vorher/Nachher-Slider ist randlos mit ca. 740 px Höhe.

---

## 3. Typografie

| Rolle | Schrift | Größe D / T / M | Gewicht / Stil | Zeilenhöhe | Laufweite |
|---|---|---|---|---|---|
| Display (H1 Hero) | Saira | 124 / 66 / 44 px | 800 italic, VERSALIEN | 0,88 | −0,012 em |
| H2 Section | Saira | 78 (101 im Slider) / 41 / 34 px | 800 italic, VERSALIEN | 0,92 | −0,01 em |
| H3 Karte | Saira | 20 / 15 / 15 px | 700, VERSALIEN | 1,15 | 0 |
| Eyebrow / Kapitel | Saira | 12–14 / 11 px | 600, VERSALIEN | normal | **0,40–0,42 em** |
| Lead | Saira | 22 / 16 / 16 px | 400 | 1,45 | 0 |
| Fließtext | Inter / Saira gemischt | 13–15 px | 400 | 1,6 | 0 |
| Preis | Saira / Inter | 24–28 px | 800 / 700 | – | 0 |
| Button | Saira | 15 px | 700, VERSALIEN | – | **0,22 em** |
| Nav | Saira | 14 px | 600 | – | 0,04 em |

**Charakter:** Saira ist eine technische, leicht eckige Grotesk. In 800 italic wirkt sie wie Motorsport-Startnummern. Inter dient als neutraler Lesetext.

**Hierarchie:** Die Größensprünge sind sehr groß (Display ≈ 9 × Fließtext). Ein Wort der Headline wird jeweils rot eingefärbt („… OF **DRY.**“), das ist das zentrale Wiedererkennungsmuster.

**Mobile-Lesbarkeit:**
- ✅ Die Headlines skalieren sauber (44 px), der Lead ist 16 px groß.
- ⚠️ Eyebrows mit 11 px und 0,42 em Laufweite sind schwer lesbar und brechen in schmalen Karten unschön um („XXL FLAGGEN- / EDITION“).
- ⚠️ Lange Produktnamen in Versalien brechen ohne Silbentrennung mitten im Wort („WASCHHANDSCH / UHE“).
- ⚠️ Die Kartenbeschreibung mit 13 px ist bei 64 % Weiß-Opazität zu blass.

---

## 4. Farben

| Rolle | Wert | Einsatz |
|---|---|---|
| Hintergrund Basis | `#0B0D10` | Body, Header (72 % + Blur) |
| Hintergrund tief | `#050506` / `#070708` | Hero, Bestseller-Verlauf |
| Fläche / Karte | Verlauf `#141418 → #0E0E11` | Produktkarten, Trust-Kacheln |
| Text | `#F3F4F6` | Headlines, Text |
| Text gedämpft | `rgba(244,244,242,.64)` | Sublines, Beschreibungen |
| Akzent | `#E02A1E` – `#FF4A3D` (mehrere Töne) | CTA, Badges, Eyebrows, Linien |
| Linien | ca. `rgba(255,255,255,.08)` | Kartenrahmen, Footer-Trenner |

- **Hell/Dunkel:** praktisch 100 % dunkel. Helle Flächen tauchen nur ungewollt auf (Warenkorb-Summenbox, Varianten-Auswahl, PayPal-Button) und wirken dort als Bruch.
- **Verläufe:** Buttons haben einen vertikalen Verlauf (Hell- zu Dunkelrot), die Announcement-Bar einen horizontal animierten Rot-Verlauf (9-s-Loop), Sections einen radialen Rot-Glow am Kopf (`radial-gradient(80% 60% at 50% 0, rgba(212,39,28,.14), transparent 70%)`), die Footer-Headline einen Silber-Metallic-Verlauf.
- **Glow:** Der Primär-CTA hat `box-shadow: 0 10px 40px rgba(224,42,30,.45)`, also einen „Rücklicht“-Effekt.
- **Kontraste:** Weiß auf Schwarz ist hervorragend (ca. 18:1). Rot `#E02A1E` auf `#0B0D10` liegt bei ca. 4,3:1, für kleine Eyebrows ist das grenzwertig. Gedämpfter Text mit 64 % liegt bei ca. 7:1 und ist ok.
- **Problem:** Es gibt mindestens fünf verschiedene Rottöne (`#E02A1E`, `#FF4A3D`, `#FF3D2E`, `#D4271C`, `#B52216`), und Horizon-Defaults mischen sich ein.

---

## 5. Bildsprache

- **Produktfotografie:** Low-Key-Fotografie: Das Produkt liegt auf schwarzem, nassem Autolack (Motorhaube, Scheinwerfer im Anschnitt). Dramatisches Streiflicht, Wassertropfen als Textur. Gleiche Perspektive und gleicher Bildaufbau über die ganze Serie, deshalb wirkt das Grid sehr ruhig.
- **Lifestyle:** Ein Hero-Supersportwagen in einer Neon-Tiefgarage (Video-Standbild bzw. Animation), Hände bei der Anwendung, UGC-Stories im Hochformat.
- **Bildausschnitte:** Karten im Format ≈ 0,91 : 1 (leicht hoch), Varianten-Kacheln 0,6 : 1 (Hochformat), Bundles 3 : 2, UGC 9 : 16, Produktgalerie 1 : 1.
- **Freisteller vs. Szene:** fast ausschließlich Szenenbilder. Freisteller gibt es nicht, deshalb funktioniert die dunkle Karte als Bühne.
- **Overlays:** Der Hero hat einen Doppelverlauf (links 92 % → 5 % Schwarz, unten 90 %), damit der Text lesbar bleibt. Auf der Kollektionsseite liegt ein dunkles Bildbanner (ca. 50 % abgedunkelt) hinter der Headline. Varianten-Kacheln haben einen Verlauf nach unten für Ländercode und Name.
- **Weißraum:** „Schwarzraum“, also viel leere dunkle Fläche um die Headlines. Die Karten selbst sind dicht gepackt.
- **Schwächen:** Uneinheitliche Grafiken (Bundle-Bilder mit eingebranntem Text, abgeschnittene Text-Grafiken bei zwei Kollektionsprodukten). Das bricht die sonst konsistente Fotostrecke.

---

## 6. Komponenten

### Header ([desktop](hydrozz/header-desktop.png), [mobile](hydrozz/header-mobile.png))
- Announcement-Bar mit roter Verlaufsfläche und rotierenden Botschaften (Rückgabe, Versand, Zahlung, Versandpartner).
- Header 75 px (Desktop) bzw. 67 px (Mobile), `rgba(11,13,16,.72)` mit Backdrop-Blur, Sticky. Er blendet sich beim Scrollen nach unten aus und beim Hochscrollen wieder ein.
- Desktop: Logo links, Nav-Links zentriert (14 px, 600), Icons rechts. Aktiver Link mit roter Unterstreichung ([collection-desktop](hydrozz/collection-desktop.png)).
- Mobile: Burger links, Logo, Such- und Warenkorb-Icon rechts. **Die Icon-Trefferfläche beträgt nur 22 × 22 px**, also unter der 44-px-Empfehlung.

### Buttons
- **Primär:** Pill (`border-radius: 99px`), Rot-Verlauf, 64 px hoch, 15 px Versalien mit 0,22 em Laufweite, Glow-Schatten. Hover: Anhebung plus stärkerer Glow ([hover](hydrozz/home-desktop-hero-button-hover.png)).
- **Sekundär:** Text-Link in Versalien mit weiter Laufweite und rotem Pfeil („BESTSELLER →“).
- **Outline-Pill:** roter Rahmen, Versalien („ANSEHEN“) in Bundle-Karten.
- **Inkonsistent:** Footer-CTA mit 12 px Radius in Normalschreibung, Produktseite mit 14 px Radius, Warenkorb-App eckig.

### Badges
- Rabatt-Pill in Rot („−33 %“), weiße Versalien mit 11 px.
- Status-Pill als dunkle Outline („Aktuell ausverkauft“).
- „SET“ / „SPARE x €“ als rote Pill.

### Produktkarten ([best](hydrozz/home-desktop-best.png), [hover](hydrozz/home-desktop-cards-hover.png))
- Dunkle Karte mit vertikalem Verlauf, 1 px Rahmen in ca. 8 % Weiß und ca. 16 px Radius.
- Aufbau: Bild (oben, randlos) → Kategorie-Eyebrow → Titel H3 in Versalien → Kurz-Nutzen → Preis groß und Streichpreis grau → vollbreiter Pill-Button „In den Warenkorb“.
- Hover: Karte hebt sich leicht an, das Bild zoomt langsam (0,7 s), der Rahmen hellt auf.
- Kollektionsseite: kompaktere Karte mit rundem „+“-Quick-Add-Button statt Textbutton.

### Preisdarstellung
- Aktueller Preis groß und fett (24–28 px), Streichpreis daneben klein, grau, durchgestrichen.
- Im Warenkorb-Drawer: „(Du sparst 10,00 €)“ in Grün, eine weitere Farbe, die nicht zum System gehört.

### Trust-Elemente ([trust](hydrozz/home-desktop-trust.png))
- Startseite: 4 Kacheln (Versand, Versanddienstleister, Zahlung, Rückgabe) mit kurzem roten Strich oben, Titel in Versalien und einer Zeile Erklärung. Keine Icons, sehr ruhig.
- Produktseite: 2×2-Kacheln mit Icon und rotem Rahmen sowie Payment-Logos unter dem CTA.
- Footer: Payment-Icons, „Preise zzgl. Versandkosten“.

### FAQ
- Kollektionsseite: zweispaltig, links Headline und Kontakt-Hinweis, rechts Akkordeon mit „+“-Icons und Trennlinien.
- Produktseite: einspaltiges Akkordeon (Horizon-Standard).

### Newsletter
- **Nicht vorhanden.** Es gibt kein Newsletter-Formular, kein Pop-up und kein Exit-Intent. Nach 12 s erscheint nichts ([after-12s](hydrozz/home-mobile-after-12s.png)).

### Footer ([desktop](hydrozz/footer-desktop.png), [mobile](hydrozz/footer-mobile.png))
- Oben eine Abschluss-Headline mit Metallic-Verlauf und einem CTA, darüber ein roter Glow.
- Darunter 4 Spalten: großes Logo mit Kurzbeschreibung und Social-Links, Spalten Shop, Hilfe und Rechtliches. Spaltentitel in Rot, Versalien und weiter Laufweite.
- Unten Payment-Icons und Copyright.
- Mobile: alles untereinander, keine Akkordeons, der Footer ist dadurch ca. 1370 px hoch.

### Mobile-Menü ([menu-open](hydrozz/header-mobile-menu-open.png))
- Vollflächiges Overlay mit großen Links (≈ 28 px), Trennlinien und rotem Pfeil je Zeile, Versand-Hinweis am Ende.
- **Fehler:** Der Overlay-Hintergrund ist teilweise transparent, sodass Hero-Headline und Menülinks übereinanderliegen. Das ist ein klarer Lesbarkeitsfehler.

### Warenkorb / Checkout-Hinweise ([drawer](hydrozz/cart-mobile-drawer.png), [Seite](hydrozz/cart-desktop.png))
- Drawer (App): Fortschrittsbalken „Noch x € bis Gratisversand“, Cross-Sell „Oft dazu gekauft“, Rabattcode-Feld und CTA „Sicher zur Kasse · Betrag“.
- Gestaltung bricht mit dem System: eckige Buttons, weiße Mengen-Stepper, grüner Spar-Hinweis, keine Saira.
- Warenkorb-Seite: graue Fläche plus weiße Summenbox mit schwarzem Button. Das ist ein kompletter Stilbruch.

### Produktseite ([desktop](hydrozz/product-desktop.png), [full](hydrozz/product-desktop-full.png))
- Zweispaltig: Galerie links (große Bilder, randlos), Buybox rechts.
- Buybox: H1 (32 px, Saira italic) → Subline → Preis → 4 Häkchen-Nutzen → Mengenstaffel als Radio-Karten („1x“, „2x – Bestseller“) → CTA → PayPal-Express → Payment-Logos → 2×2-Trust-Kacheln.
- Darunter: „So funktioniert es“ in 3 Schritten (Bild/Text im Wechsel), eine Story-Section, FAQ-Akkordeon und der Abschluss-CTA.
- Mobile: Sticky-Add-to-Cart-Leiste unten (Thumbnail, Titel, Preis, Button), die nach dem Scrollen erscheint ([scrolled](hydrozz/product-mobile-scrolled.png)).
- Die Buybox ist auf Desktop **nicht** sticky.

---

## 7. Motion & Interaktion

| Element | Verhalten | Dauer / Easing | Bewertung |
|---|---|---|---|
| Scroll-Reveal (`.h2-rv`) | Fade + translateY | 0,8 s `cubic-bezier(.2,.7,.2,1)` | ✅ dezent |
| Produktkarte Hover | Anheben + Schatten, Bild-Zoom | 0,25 s / 0,7 s | ✅ hochwertig |
| Button Hover | Anheben, Glow verstärkt | 0,2 s | ✅ |
| Nav-Link | rote Unterstreichung wächst | 0,6 s (Breite) | ✅ |
| Announcement-Bar | Verlauf wandert endlos | 9 s Loop | ⚠️ unruhig, stört bei `prefers-reduced-motion` |
| Hero-Hintergrund | langsamer Zoom/Drift | 24 s Loop | ⚠️ grenzwertig, kostet Akku |
| Lichtstreifen im Hero | diagonale Linie | statisch / animiert | ✅ als Akzent |
| Vorher/Nachher | Drag-Slider mit Griff | direkt | ✅ starke Interaktion |
| Quick-Add-Buttons | Spring-Bounce `cubic-bezier(.34,1.56,.64,1)` | 0,15 s | ⚠️ verspielt |
| Mobile-Menü | Einblenden | 0,35 s | ❌ transparente Überlagerung |

- **Video:** Auf der Startseite gibt es kein `<video>`-Element. Der Hero ist ein Bild bzw. eine CSS-Animation. Die UGC-Kacheln zeigen Play-Icons (Video bei Klick).
- **Dezent:** Reveals, Karten-Hover, Nav-Unterstreichung.
- **Übertrieben:** Dauer-Animationen (Bar, Hero-Drift), Glow auf jedem Button, Bounce-Easing.

---

## 8. Mobile Experience

- **Navigation:** Burger links, Logo daneben, Suche und Warenkorb rechts. Die Icons sind zu klein (22 px Trefferfläche). Das Menü ist vollflächig mit großen Links, aber transparent.
- **Hero:** Das Bild steht oben (ca. 45 % der Höhe), Text und CTA darunter auf Schwarz, also **nicht** über dem Bild. Das ist gut lesbar und eine sinnvolle Mobile-Entscheidung. Der CTA ist 64 px hoch und gut zu treffen.
- **Produktkarten:** 2 Spalten à 168 px. Durch die Versalien-Titel werden die Karten sehr hoch (ca. 480 px). Eyebrow, Titel, Nutzen, Preis und Button sind zu viel Inhalt für diese Breite.
- **Touch-Targets:** Karten-Buttons 47 px ✅, Hero-CTA 64 px ✅, Header-Icons 22 px ❌, Mengen-Stepper im Drawer ca. 36 px ⚠️.
- **Scrollverhalten:** Der Header blendet sich beim Runterscrollen aus und beim Hochscrollen ein, so bleibt viel Inhaltsfläche frei. Die Sections folgen ohne horizontale Karussells (außer im Warenkorb-Cross-Sell).
- **Lesbarkeit:** Lead und Text mit 16 px sind gut. Eyebrows mit 11 px und weiter Laufweite sind zu klein.
- **Sticky-Elemente:** Announcement-Bar und Header (Smart-Hide), auf der Produktseite eine Sticky-ATC-Leiste unten.
- **Mobile-spezifisch:** Hero-Layout gestapelt, Grids auf 2 Spalten, Footer gestapelt ohne Akkordeon (sehr lang).

---

## 9. Conversion-Psychologie

**Reihenfolge der Startseite:**
1. Hero (Emotion + 1 CTA + Mini-Produktkarte mit Preis unten rechts)
2. Bestseller (sofort kaufbar, mit Preis und Button)
3. Varianten-Kollektion (Identifikation)
4. Vorher/Nachher (Beweis)
5. 4 USPs (Rationalisierung)
6. Bundles (Warenkorbwert)
7. Community / UGC (Social Proof)
8. Trust-Kacheln (Risikoabbau)
9. Footer-CTA (letzte Chance)

**Vertrauenssignale:** Rückgaberecht, Versandkostengrenze, Versanddienstleister mit Tracking, Zahlarten, UGC-Videos. Es gibt keine Sternebewertungen auf der Startseite.

**CTAs:** genau ein Primär-CTA pro Bildschirm. Sekundäre Aktionen sind als Text-Link gestaltet. Auf Karten steht direkt „In den Warenkorb“ (ohne Umweg über die Produktseite).

**Produktdarstellung:** Nutzen vor Merkmal (Häkchen-Liste), Mengenstaffel mit „Bestseller“-Markierung (Anker-Effekt), Streichpreise.

**Kaufbarrieren, die abgebaut werden:** Versandkostenschwelle mit Fortschrittsbalken, Express-Checkout (PayPal), Payment-Logos, Rückgabe-Hinweis direkt unter dem CTA.

**Für carbiente übernehmen (als Prinzip):**
- ✅ Bestseller direkt nach dem Hero, kaufbar aus der Karte.
- ✅ Ein Primär-CTA pro Bildschirm, Sekundär-CTA als Text-Link mit Pfeil.
- ✅ Vorher/Nachher-Slider (bei uns: Innenraum ohne / mit Ambientelicht). Das ist der stärkste Beweis für Licht.
- ✅ Trust-Kacheln ohne Icon-Lärm.
- ✅ Fortschrittsbalken bis zur Gratisversand-Grenze (50 € DE, über die Theme-Einstellung).
- ✅ Sticky-ATC-Leiste auf Mobile.
- ✅ Häkchen-Nutzenliste in der Buybox.
- ✅ Nummerierte Kapitel-Eyebrows für Ratgeber-, Einbau- und Schritt-Inhalte.
- ⚠️ Mengenstaffel / „Bestseller“-Markierung nur mit echten Daten. Keine erfundenen Labels.
- ❌ Streichpreise / „−33 %“ nur bei echten Preisreduzierungen (Preisangabenverordnung, niedrigster Preis der letzten 30 Tage).

---

## 10. Was wir NICHT kopieren

**Rechtlich / markenrechtlich:**
- Name, Logo, Blitz-Signet, Schriftzug und Wortmarke von hydrozz.
- Sämtliche Texte und Claims (z. B. „The next level of …“, „One towel. One pass.“, „Represent your roots“, „Built with the community“, „Nie wieder …“), auch nicht sinngemäß übersetzt.
- Bilder, Videos, UGC, Produktfotos, Hero-Szene (Supersportwagen in Neon-Garage), Flaggen-Motive.
- Die konkrete Kombination aus Saira 800 italic in Versalien, Rot-Verlauf und Glow. Das ist deren visuelle Signatur. Wir nutzen bewusst Archivo, Cyan und Normalschreibung.
- Konkrete Rabattstaffeln, „Bestseller“-Labels, Spar-Claims.
- Kapitel-Nummerierung mit Gedankenstrich und weiter Laufweite **nicht 1:1**. Bei uns bekommt sie ein eigenes Format (siehe Design-Sprache, „Kapitelmarke“).

**Passt zu Trockentüchern, aber nicht zu Ambientebeleuchtung:**
- Nasser Lack und Wassertropfen als Bildthema → bei uns Innenraum bei Nacht und Lichtlinien.
- Aggressives Rot (Gefahr, Bremslicht) → Ambientelicht ist ruhig und atmosphärisch, deshalb Cyan.
- Dauerhaft dunkle Seite → wir brauchen helle, sachliche Flächen für Technik-Infos (Kompatibilität, Einbau, Lieferumfang) und setzen Dunkel gezielt als Nachtbühne ein.
- Versalien-Kursiv-Headlines → wirken bei Erklär- und Ratgeber-Inhalten zu laut. Unser Ton ist sachlich-kompetent.
- Länder- und Identitäts-Kollektionen, Community-UGC → für uns aktuell nicht vorgesehen (keine Social Proofs bis zu echten Inhalten).
- Flaggen-Kacheln (Hochformat 0,6 : 1) → bei uns ggf. Farb- oder Set-Varianten, aber nur mit echten Daten.

**Fehler, die wir vermeiden:**
- Transparentes Mobile-Menü, Header-Icons mit 22 px, mehrere Akzent-Töne, App-Widgets im Fremdstil, helle Summenbox auf dunkler Seite, Endlos-Animationen ohne `prefers-reduced-motion`, inkonsistente Container-Breiten (1296 vs. 1200 px), Versalien-Titel ohne Silbentrennung in schmalen Karten.
