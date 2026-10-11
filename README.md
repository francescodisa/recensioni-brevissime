# Recensioni brevissime di libri difficili

Archivio delle recensioni di Francesco D'Isa (@disa_fran), consultabile come sito statico: una scheda a caso in home, archivio con ricerca per autore e titolo, versione italiana e inglese.

## Struttura

- `index.html` contiene tutta la pagina (grafica, logica, interfaccia).
- `reviews.json` contiene i dati; è l'unico file da modificare per aggiungere o correggere recensioni.
- `fonts/` contiene Old Standard TT (licenza SIL Open Font License), così il sito non dipende da servizi esterni.

## Pubblicare su GitHub Pages

1. Crea un repository e carica il contenuto di questa cartella nella radice.
2. In Settings, Pages, scegli "Deploy from a branch", ramo `main`, cartella `/ (root)`.
3. Dopo un minuto il sito è online all'indirizzo `https://<utente>.github.io/<repository>/`.

Il sito legge `reviews.json` con una richiesta `fetch`, quindi aprendo `index.html` con doppio clic da disco non mostra le schede. Per provarlo in locale basta avviare un server, per esempio `python3 -m http.server` nella cartella e aprire `http://localhost:8000`.

## Aggiungere una recensione

Ogni recensione è un oggetto nell'array `reviews` di `reviews.json`:

```json
{
  "id": "autore-titolo",
  "author": "Nome Cognome",
  "authorSort": "Cognome",
  "vote": 4,
  "it": { "title": "Titolo", "review": "Testo della recensione.", "plot": "Trama in una riga" },
  "en": { "title": "Title", "review": "Review text.", "plot": "One-line plot" }
}
```

L'`id` deve essere unico (minuscolo, senza spazi) e viene usato anche per il collegamento diretto alla scheda (`index.html#id`). Il voto va da 1 a 5. Con la sola modifica del JSON la scheda compare in home e in archivio.

## Note

Il testo delle recensioni appartiene all'autore. Il codice e la grafica sono pensati per questo progetto; i font sono distribuiti con la loro licenza.
