# JGNet Schlau Content

Artikel und Bilder für das Schlau Portal.

## Struktur

```
articles.json    # Artikeldaten (Bestelltool)
rackplaner.json  # Welche Artikel der Rackplaner beim Planen anbietet — Kategorie → Artikelnummern
RACKPLANER.md    # Anleitung dazu
imgs/            # Produktbilder (1.png, 2.png, ...)
```

## Artikel hinzufügen

1. Bild in `imgs/` hinzufügen (z.B. `19.png`)
2. Artikel in `articles.json` ergänzen:

```json
{
  "typ": "Net",
  "bild": "19.png",
  "hersteller": "Hersteller Name",
  "name": "Produkt Name",
  "artikelnummer": "ABC123",
  "ve": "1 Stk",
  "link": "https://example.com/produkt"
}
```

3. Pull Request erstellen
4. Nach Merge wird automatisch deployed

## Artikel im Rackplaner anbieten

`articles.json` bleibt dafür unverändert. Die Artikelnummer kommt zusätzlich in die passende Kategorie in `rackplaner.json` — direkt im Browser editierbar, Anleitung und Kategorien in [RACKPLANER.md](RACKPLANER.md). Danach im Portal **„Sync from GitHub“**; der Sync meldet unbekannte Kategorien und Nummern, die es in `articles.json` nicht gibt.

## Typen

- `Net` - Netzwerk-Komponenten
- `230` - Elektro-Komponenten
