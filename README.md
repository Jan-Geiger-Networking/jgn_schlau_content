# Schlau Artikelliste

Hier liegt die Artikelliste, aus der das **Bestelltool** im Schlau Portal und die **Schrankplanung** im Rackplaner ihre Artikel holen. Wer hier etwas ändert, ändert es für alle — nach dem nächsten „Sync from GitHub" im Portal.

## Was liegt hier?

| Datei / Ordner | Wofür |
|---|---|
| `articles.json` | Alle Artikel fürs Bestelltool (rund 100 000 Stück, 44 MB). Bitte nicht im Browser bearbeiten — die Datei ist dafür zu groß. |
| `rackplaner.json` | Eine kurze Liste: welche Artikel der Rackplaner beim Planen eines Schranks anbietet. **Die darf jeder im Browser bearbeiten**, Anleitung weiter unten. |
| `imgs/` | Die Produktbilder (`1.png`, `2.png`, `42.jpg` …). |

## Wie ein Artikel aussieht

Jeder Artikel in `articles.json` hat diese Felder:

```json
{
  "typ": "Net",
  "bild": "19.png",
  "hersteller": "Telegärtner",
  "name": "Anschlussdose AMJ45 8/8 K Up/50 Cat.6A alpinweiß",
  "artikelnummer": "J00020A0505",
  "ve": "1 Stk",
  "link": "https://www.hersteller.de/produkt",
  "ean": "4018359123456",
  "datenblatt": "https://www.hersteller.de/datenblatt.pdf"
}
```

- **typ** — die Gruppe im Bestelltool (Tabelle unten).
- **bild** — Dateiname im Ordner `imgs/`, darf leer bleiben.
- **hersteller, name, artikelnummer** — so wie sie auf der Rechnung des Großhändlers stehen.
- **ve** — Verpackungseinheit, z. B. `1 Stk`, `100 Stk`, `50 m`.
- **link, ean, datenblatt** — freiwillig.

### Die Typen

| typ | Was gehört hinein | Beispiel |
|---|---|---|
| `Net` | Netzwerk: Dosen, Patchfelder, Keystones, Kabel, Schränke, Switches | Anschlussdose Cat.6A |
| `LWL` | Glasfaser: Pigtails, Spleißboxen, LWL-Kabel | OpDAT Pigtail LC, OM4 |
| `230` | Elektro-Installation: Steckdosen, Schalter, Leitungen | SCHUKO-Steckdose 16 A |
| `Gira` | Schalterprogramm Gira | Wippe Reinweiß seidenmatt |
| `Wago` | Klemmen von WAGO | Verbindungsklemme 3 × 4 mm² |
| `KTS` | Kabeltragsysteme: Kabelrinnen, Halter, Deckel | Kabelrinne RKS-Magic 35 |
| `SiBe` | Sicherheitsbeleuchtung: Leuchten, Piktogramme | Piktogrammscheibe 1016 |
| `Wuerth` | Alles von Würth: Befestigung, Werkzeug, Schutzausrüstung | Absperrband rot/weiß |

Neue Typen bitte vorher absprechen — das Bestelltool muss sie kennen.

## Einen neuen Artikel ins Bestelltool bekommen

Am einfachsten: im Bestelltool oder im Rackplaner den Artikel als **Extra-Artikel** eintragen (Name, Hersteller, Artikelnummer, VE, Link). Die Verwaltung bekommt dann automatisch eine Mail und nimmt ihn hier auf. Du musst dafür nichts in diesem Repo machen.

Wer die Datei selbst pflegt (lokaler Klon, Editor): Bild nach `imgs/`, Eintrag in `articles.json` wie oben, Commit, Push. Danach im Portal **„Sync from GitHub"**.

## Artikel im Rackplaner anbieten

Der Rackplaner kann Schränke planen und das Material dafür bestellen. Dabei zeigt er beim Planen **nur Artikel, die in `rackplaner.json` stehen** — sonst wäre die Auswahl bei 100 000 Artikeln unbrauchbar. Fehlt dir beim Planen ein Artikel, trägst du ihn selbst ein. Das dauert zwei Minuten und geht direkt hier im Browser.

**Was du brauchst:** die Artikelnummer, genau so, wie sie im Bestelltool steht (Groß-/Kleinschreibung, Punkte, Bindestriche). Der Artikel muss im Bestelltool schon existieren; wenn nicht, erst als Extra-Artikel melden (siehe oben).

**So geht's:**

1. Klicke oben auf die Datei `rackplaner.json`.
2. Klicke auf den Stift (rechts oben, „Edit this file").
3. Suche die passende Kategorie — die Namen stehen in Anführungszeichen, z. B. `"connector"`.
4. Füge die Artikelnummer als neue Zeile in die Liste darunter ein: in Anführungszeichen, und die Zeile davor bekommt ein Komma ans Ende. So sieht ein Stück der Datei aus:
   ```json
   "connector": [
     "N420.960",
     "N420.961"
   ],
   "patchfeld": [
     "N521.661"
   ],
   ```
5. Klicke unten auf **„Commit changes"**, schreib kurz, was du gemacht hast (z. B. „LANmark-6A ULTIM als Connector"), und bestätige.
6. Sag einem Admin Bescheid. Der klickt im Portal auf **„Sync from GitHub"**. Danach ist der Artikel im Rackplaner wählbar.

Wenn ein Eintrag nicht stimmt (Tippfehler, unbekannte Kategorie, Artikelnummer gibt es nicht), meldet der Sync das dem Admin und lässt genau diesen Eintrag weg — alles andere funktioniert weiter. Es kann also nichts kaputtgehen.

### Die Kategorien

| Kategorie | Was gehört hinein | Beispiel |
|---|---|---|
| `schrank` | Netzwerk- und Serverschränke, Wandgehäuse | 19"-Standschrank 42 HE |
| `patchfeld` | Patchfeld-Träger für Kupfer, leer oder bestückt | Patch Panel 24 Snap-In |
| `connector` | Module/Keystones, die ins Patchfeld geklickt werden | LANmark-6A ULTIM |
| `lwl-patchfeld` | Spleißboxen, LWL-Verteiler | Spleißbox 19" 1 HE |
| `pigtail` | Pigtails, einzeln oder im Set | ST Pigtail 9/125 µm OS2, 2 m |
| `rangierfeld` | Rangier- und Kabelführungspanels | Rangierpanel mit Stahlbügeln |
| `switch` | Switches, Router, Firewalls, Medienkonverter | UniFi Switch 24 PoE |
| `strom` | Steckdosenleisten, PDU, USV | 19" Steckdosenleiste 8-fach |
| `server` | Server, NAS | — |
| `zubehoer` | Bügel, Fachböden, Käfigmuttern, Blindplatten, Lüfter | Kabelführungsbügel 65×125 mm |

### Regeln

- Jede Artikelnummer steht in **genau einer** Kategorie.
- Nur Kategorien aus der Tabelle. Eine neue Kategorie kann der Rackplaner nicht verwenden — sprich sie vorher ab.
- Nicht sicher, welche Kategorie? Nimm die, bei der du den Artikel beim Planen **suchen** würdest.
- Falsch eingetragen ist nicht schlimm: Zeile löschen, wieder „Commit changes", Sync.
- Kabel, Werkzeug und Verbrauchsmaterial gehören nicht hinein. Der Rackplaner plant nur, was im Schrank verbaut wird.
