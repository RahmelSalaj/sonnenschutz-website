# Sonnenschutz-Website — Shopify-Theme

Vollwertiges Shopify-Theme (Online Store 2.0) für den Shop rund um den
**faltbaren Auto-Sonnenschutz für die Frontscheibe**. Deutsch, EUR, bewusst ohne
Bilder gebaut — überall, wo später Fotos hinkommen, zeigt das Theme saubere
Platzhalter. Farben, Schrift und Logo sind im Theme-Editor einstellbar
(Anpassen → Theme-Einstellungen), der Shop-Name wird automatisch aus Shopify
übernommen.

## Struktur

```
layout/      theme.liquid (Grundgerüst), password.liquid
config/      settings_schema.json (Theme-Einstellungen), settings_data.json
locales/     de.default.json
sections/    Header, Footer, Hero, Vorteile, So funktioniert's, FAQ,
             Text mit Button + main-* für Produkt, Kollektion, Warenkorb,
             Seite, Blog, Artikel, Suche, 404, Passwortseite
snippets/    product-card.liquid
templates/   JSON-Templates (OS 2.0) — Startseiten-Inhalte in index.json
assets/      base.css (komplettes Styling)
```

## Mit Shopify verbinden

1. Shopify-Admin → **Onlineshop → Themes**
2. **Theme hinzufügen → Aus GitHub verbinden**
3. Dieses Repository und den Branch `main` auswählen
4. Vorschau prüfen, dann **Veröffentlichen**

Danach synchronisiert Shopify jeden Push auf `main` automatisch ins Theme —
und Änderungen im Theme-Editor werden als Commits zurück ins Repo geschrieben.

## Wichtig: Nur Shopify-Format

Shopify kann mit statischen `index.html`-Dateien nichts anfangen. Inhalte
gehören in `sections/*.liquid` (mit `{% schema %}` am Ende, damit sie im
Editor auftauchen) und werden über `templates/*.json` zusammengesteckt.
CSS liegt in `assets/` und wird per `{{ 'base.css' | asset_url | stylesheet_tag }}`
geladen; Bilder im Editor hochladen (image_picker) oder in `assets/` ablegen
und per `asset_url` referenzieren.
