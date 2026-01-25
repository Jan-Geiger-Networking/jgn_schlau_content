# JGNet Schlau Content

Artikel und Bilder für das Schlau Portal.

## Struktur

```
articles.json    # Artikeldaten
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

## Typen

- `Net` - Netzwerk-Komponenten
- `230` - Elektro-Komponenten
