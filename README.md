# carbiente – Shopify Theme

Theme für **carbiente**, Ambientebeleuchtung fürs Auto zum Selbsteinbau (Lichtsets, LED-Streifen, Zubehör).
Basis ist das [Shopify Skeleton Theme](https://github.com/Shopify/skeleton-theme), ausgebaut zu einem Online Store 2.0 Theme mit Sections, JSON-Templates und Theme-Editor-Einstellungen.

- **Sprache:** Deutsch (`locales/de.default.json`), Ansprache „du“
- **Märkte:** DE / AT / CH, Gratisversand ab 50 € (nur DE, Theme-Einstellung)
- **Prinzipien:** Mobile First, WCAG 2.2 AA, 48-px-Touch-Targets, kein Tracking, keine Drittanbieter-Skripte, Platzhalter klar als „PLATZHALTER“ gekennzeichnet

## Entwicklung

Voraussetzung: aktuelle [Shopify CLI](https://shopify.dev/docs/api/shopify-cli), optional die [Shopify Liquid VS Code Extension](https://shopify.dev/docs/storefronts/themes/tools/shopify-liquid-vscode).

```bash
# Lokale Vorschau gegen das Development-Theme (nie gegen das Live-Theme)
shopify theme dev --path . --theme <development-theme-id> --port 9292
# → http://127.0.0.1:9292

# Prüfung vor jedem Commit
shopify theme check --path .
```

Hinweise:
- Ist der Shop passwortgeschützt, `theme dev` mit `--store-password` starten (oder Umgebungsvariable `SHOPIFY_FLAG_STORE_PASSWORD`). Sonst leitet die Vorschau zeitweise auf `/password` um.
- Während `theme dev` läuft, Dateien nicht mit `sed -i` bearbeiten. Die temporären Dateien verursachen Upload-Fehler.
- Kein `shopify theme push`/`publish` auf das Live-Theme ohne ausdrückliche Freigabe.

## Struktur

```
.
├── assets/        critical.css (Reset, Typo, Buttons, Grid, Media, Utilities)
├── config/        settings_schema.json (Farbschemata, Fonts, Layout, Versand), settings_data.json
├── layout/        theme.liquid, password.liquid
├── locales/       de.default.json (Storefront), de/en .schema.json (Theme-Editor)
├── sections/      Startseiten-Sections, main-* Templates, Header/Footer-Gruppen
├── snippets/      css-variables, image, product-card, price, breadcrumbs, pagination, light-line, …
├── templates/     JSON-Templates (index, collection, product, …), index.styleguide.json
└── docs/          Design-Referenz und Design-Sprache
```

Architekturregeln (Schema, LiquidDoc, `{% stylesheet %}`/`{% javascript %}` pro Komponente, Locales) stehen in [`AGENTS.md`](./AGENTS.md).

## Design-System

| Was | Wo |
|---|---|
| Verbindliche Design-Sprache (Prinzipien, Tokens, Komponenten, Mobile, Do's & Don'ts, Liquid/CSS-Vorlagen) | [`docs/design-reference/design-language.md`](./docs/design-reference/design-language.md) |
| Referenz-Analyse hydrozz.de (nur Prinzipien) | [`docs/design-reference/hydrozz-analysis.md`](./docs/design-reference/hydrozz-analysis.md) |
| Design-Tokens (CSS Custom Properties aus Theme-Settings) | [`snippets/css-variables.liquid`](./snippets/css-variables.liquid) |
| Globale Styles und Utilities | [`assets/critical.css`](./assets/critical.css) |
| Live-Styleguide | Template `index.styleguide`, Vorschau unter `/?view=styleguide` |
| Review-Agent für UI-Schritte | [`.claude/agents/design-language-guardian.md`](./.claude/agents/design-language-guardian.md) |

Kurzfassung: helle Basis (`scheme-1`/`scheme-2`) mit dunklen „Nachtbühnen“ (`scheme-3`), Akzent Midnight Cyan (`#006F86` hell / `#3DD5EE` dunkel), Archivo für Headlines, Inter für Text, Pill-Buttons, Produktbilder auf dunkler Bühne (`.media--stage`).

Die Screenshots unter `docs/design-reference/hydrozz/` bleiben lokal (`.gitignore`, Fremdmaterial).

## Arbeitsweise

Umsetzung in einzeln freigegebenen Schritten. Pro UI-Schritt:

1. Plan mit betroffenen Dateien → Plan-Review durch den `design-language-guardian`
2. Umsetzung
3. `shopify theme check` + Playwright-Screenshots der lokalen Vorschau (390 / 768 / 1440 px)
4. Code-Review durch den Guardian
5. Commit erst nach Freigabe

| Schritt | Inhalt | Stand |
|---|---|---|
| 1–3 | Briefing, Informationsarchitektur, Design-System | ✅ |
| 4 | Basis-Layout, Tokens, deutsche Locale, OS-2.0-Templates | ✅ |
| 5 | Header (sticky, Mobile-Drawer), Announcement-Bar, Footer | ✅ |
| 6 | Startseite (12 Sections), Produktkarte, Styleguide | ✅ |
| 7 | Kollektionsseiten: Filter (Search & Discovery), Sortierung, Paginierung ohne JS-Pflicht, Breadcrumb, SEO-Text, Leerzustände | ✅ |
| 8–14 | weitere Schritte laut Projektplan (u. a. Produktseite, Warenkorb, Deployment) | offen |

## Offene Admin-Schritte

- Produkte anlegen bzw. importieren (Platzhalter-CSV liegt außerhalb des Repos in `import/`) und im Online Store veröffentlichen
- App **Shopify Search & Discovery**: Filter anlegen (Verfügbarkeit, Preis, Farbe, Länge, Steuerung)
- Metafeld-Definitionen: Kollektion `custom.seo_text` (Rich Text), Produkt `custom.kompatibilitaet`
- Kollektion `ambientebeleuchtung` anlegen (Ausweichziel im Leerzustand)
- Richtlinien (Impressum, AGB, Widerruf, Versand), Logo, Favicon, Hero-Bild, Menüs
- Optional: Theme-Einstellung „Versandinfo-URL“

## Lizenz

Basiert auf dem Shopify Skeleton Theme ([MIT](./LICENSE.md)).
