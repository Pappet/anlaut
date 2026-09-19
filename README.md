# Anlaut-Post

Lernspiel zum ersten Laut eines Wortes (Anlaut), als Progressive Web App.
Offline nutzbar, Spielstand im localStorage.

## Ablauf
Ein Paket mit Bild erscheint. Die Stimme sagt das Wort, dann (falls eine
eigene Aufnahme vorliegt) den Laut, dann "Womit fängt Fisch an?".
Das Paket in den passenden Briefkasten ziehen. 7 Pakete = eine Runde,
danach fährt das Postauto durch und ein neuer Buchstabe kommt dazu.

- Paket antippen: nochmal anhören (auch über 🔊 links unten)
- Briefkasten antippen: "L wie Löwe" (plus Laut, falls aufgenommen)
- Nach 13 Sekunden ohne Aktion kommt ein Tipp
- Falscher Kasten: Paket kommt zurück, das Wort wird erklärt

## Aussprache
Android-TTS kann Laute nicht dehnen: "lll" wird als "El El El" gelesen,
und auch Tricks wie "llllöwe" klingen schlecht. Deshalb sagt die Stimme
grundsätzlich nur ganze Wörter und "L wie Löwe".

Für echte Laute: `aufnahme.html` im Browser öffnen (HTTPS oder localhost),
die 14 Laute selbst einsprechen, optional auch die Wörter, dann
"Alle speichern". Die heruntergeladene ZIP enthält einen Ordner `sounds/`,
der neben `index.html` gehört. Das Spiel liest beim Start `sounds/index.json`
und benutzt vorhandene Dateien statt der TTS-Stimme:

    sounds/laut-L.webm     gedehnter Laut
    sounds/wort-Löwe.webm  das Wort
    sounds/index.json      Liste der vorhandenen Dateien

Fehlt eine Datei, springt die TTS-Stimme ein. Es funktioniert also auch
mit nur ein paar Aufnahmen.

## Buchstaben
Reihenfolge in `ORDER` (index.html): erst dehnbare Laute (S, M, L),
dann Vokale, zuletzt harte Laute (B, T, K, P, D).
S startet mit dem Anker "S wie Sonne" (erstes Wort der Liste).
Ähnlich klingende Paare stehen in `CONFUSE` und kommen nie zusammen
in eine Runde: B/P, D/T, M/N, F/S.
Kästen: 2 bis 3 Buchstaben → 2 Kästen, ab 6 Buchstaben → 4 Kästen.

## Bilder ersetzen
Die Wortlisten in `LETTERS` enthalten Paare [Wort, Emoji].
Emojis wurden bewusst auf eindeutige Begriffe beschränkt
(kein 🥕, weil Kinder auch "Karotte" sagen).
Für eigene Zeichnungen das Emoji durch ein <img>-Tag ersetzen.

## Veröffentlichen / Installieren / Ändern
Wie bei den anderen Spielen. Nach Änderungen `VERSION` in `sw.js` hochzählen.

## Spielstand zurücksetzen
Stern-Anzeige oben rechts 3 Sekunden gedrückt halten.
