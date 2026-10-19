# BCW Beulencenter Wuppertal - Vorschau

One-Pager für das Beulencenter Wuppertal (Linderhauser Straße 38, 42279 Wuppertal, 0172 2139306), Ersatz für beulencenter.de. Weißes Design, Archivo, Logo-Blau als Akzent.

```
public/                 die Website (index.html, images/, assets/vendor/)
netlify/functions/chat.mjs   KI-Assistent (Server-Funktion, Streaming)
dev-server.mjs          lokale Vorschau inklusive /api/chat
netlify.toml            Netlify: publish = public, functions = netlify/functions
```

Lokal ansehen:

```bash
npm install
node dev-server.mjs      # http://localhost:8798
```

## KI-Assistent
Unten rechts auf der Seite: Chat-Fenster, das Fragen zu Leistungen, Öffnungszeiten und Anfragen beantwortet (Modell `claude-haiku-5-5`, Wissen steht im `SYSTEM`-Text in `netlify/functions/chat.mjs`).
- **Veröffentlichen:** Repo mit Netlify verbinden. Unter Site configuration → Environment variables `ANTHROPIC_API_KEY` eintragen. Der Schlüssel bleibt auf dem Server und ist im Browser nie sichtbar.
- **Kosten:** Der Betrieb zahlt pro Nachricht bei Anthropic (Haiku ist sehr günstig). In der Anthropic Console ein monatliches Ausgabenlimit setzen.
- **Ohne Schlüssel oder bei Ausfall** antwortet der Chat mit festen Antworten aus der Seite (Liste `FAQ` im Skript in `public/index.html`), es geht also nichts kaputt.
- **Datenschutz:** Chat-Nachrichten gehen an Anthropic. Das gehört in die Datenschutzerklärung (zusammen mit Google Fonts und dem Kontaktformular).
- Wenn sich Öffnungszeiten, Leistungen oder Kontaktdaten ändern, den `SYSTEM`-Text und die `FAQ`-Liste mit anpassen.

## Hero
Vollbild-Foto mit Lichtbalken: Eine Lampe fährt beim Scrollen (oder mit der Maus) über das Auto, dahinter wird es hell und die Leistungen erscheinen am Wagen.

## Kontaktformular
Ohne Server: Beim Absenden öffnet sich das E-Mail-Programm mit der vorbereiteten Nachricht (mailto an info@beulencenter.de).
Direkter Versand: im `<form id="anfrage">` bei `data-endpoint=""` die URL eines Formular-Dienstes eintragen (z. B. Formspree, Web3Forms). Das Formular sendet dann JSON per POST. Honigtopf-Feld `website` ist eingebaut.

## Offen / Platzhalter
- Impressum und Datenschutz verlinken noch auf `#` (auch der Link im Formular)
- Rezensionen sind bewusst entfernt
- "Hagel-Einsätze" 2008-2012 und "bis zu 65 % günstiger" stammen von der alten Website - mit dem Inhaber bestätigen
- Öffnungszeiten laut Google: Mo, Di, Do, Fr 9-18 Uhr, Mi 9-15 Uhr (alte Seite: Mo-Fr 9-18 Uhr)
- Hol- und Bringservice, Vor-Ort-Service: stehen auf der alten Website, Details mit dem Inhaber klären
