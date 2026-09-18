# Anlaut-Post

Lernspiel zum ersten Laut eines Wortes (Anlaut), als Progressive Web App.
Offline nutzbar, Spielstand im localStorage.

## Ablauf
Ein Paket mit Bild erscheint. Die Stimme sagt dreistufig vor:
ganzes Wort → gedehnt ("Mmmmaus") → nur der Laut ("Wo gehört mmm hin?").
Das Paket in den passenden Briefkasten ziehen. 7 Pakete = eine Runde,
danach fährt das Postauto durch und ein neuer Buchstabe kommt dazu.

- Paket antippen: nochmal anhören (auch über 🔊 links unten)
- Briefkasten antippen: dessen Laut anhören
- Nach 13 Sekunden ohne Aktion kommt ein Tipp
- Falscher Kasten: Paket kommt zurück, der Laut wird erklärt

## Aussprache
Isolierte Laute werden NIE gesprochen: Android-TTS liest "lll" als "El El El".
Stattdessen spricht die Stimme immer ein echtes Wort mit gedehntem Anfang
("llllöwe", klein geschrieben, Tempo 0.66) plus "L wie Löwe".
Dehnbar ja/nein steht als `long` bei jedem Buchstaben in `LETTERS`;
harte Laute (B, T, K, P, D) werden nicht gedehnt.

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
