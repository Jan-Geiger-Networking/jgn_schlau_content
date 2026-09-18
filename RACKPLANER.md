# Artikel für den Rackplaner freischalten

Der Rackplaner kann Schränke planen und das Material dafür bestellen. Dabei bietet er **nur Artikel an, die hier eingetragen sind**. Fehlt dir beim Planen ein Artikel, trägst du ihn selbst ein — das dauert zwei Minuten.

**Was du brauchst:** die Artikelnummer, genau so, wie sie im Bestelltool steht (Groß-/Kleinschreibung, Punkte, Bindestriche).

**So geht's:**
1. Öffne die Datei `rackplaner.json` in diesem Repo und klicke auf den Stift („Edit this file").
2. Suche die passende Kategorie (Tabelle unten).
3. Füge die Artikelnummer als neue Zeile ein — in Anführungszeichen, mit Komma am Ende der Zeile davor:
   ```json
   "connector": [
     "N420.960"
   ],
   "patchfeld": [
     "N521.661"
   ],
   ```
4. Unten „Commit changes" — kurze Beschreibung, z. B. „LANmark-6A ULTIM als Connector".
5. Ein Admin klickt im Portal auf **„Sync from GitHub"**. Danach ist der Artikel im Rackplaner wählbar. Der Sync zeigt an, wenn ein Eintrag nicht stimmt.

**Kategorien**

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

**Regeln**
- Jede Artikelnummer steht in **genau einer** Kategorie.
- Nur Kategorien aus der Tabelle. Eine neue Kategorie kann der Rackplaner nicht verwenden — sprich sie vorher ab.
- Die Artikelnummer muss es in der Artikelliste geben. Gibt es den Artikel dort noch nicht, nutze im Rackplaner „Extra-Artikel"; die Verwaltung bekommt dann automatisch eine Mail und nimmt ihn auf.
- Nicht sicher, welche Kategorie? Nimm die, bei der du den Artikel beim Planen **suchen** würdest.
- Falsch eingetragen ist nicht schlimm: Zeile löschen, neu committen, Sync.

**Was nicht hierher gehört:** Kabel, Werkzeug, Verbrauchsmaterial. Der Rackplaner plant nur, was im Schrank verbaut wird.
