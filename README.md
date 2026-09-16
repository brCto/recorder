# Registratore del Quaderno

Pagina singola (`index.html`) che registra l'audio di una lezione con trascrizione in diretta (Web Speech API, `it-IT`) e la rimanda al [Quaderno delle Lezioni](https://claude.ai/artifact/7TPQ5eFeinkV4uYiLA4EsH).

Esiste perché il frame degli artifact su claude.ai non riceve il permesso del microfono: questa pagina, aperta come pagina principale su un dominio proprio, lo può chiedere normalmente.

- Aperta dal Quaderno con `?lesson=<id>&title=…`, parla con la scheda che l'ha aperta via `postMessage` (segmenti in diretta, poi audio e trascrizione a fine registrazione).
- L'audio è salvato pezzo per pezzo in IndexedDB: se la scheda muore, al riavvio propone di inviare o salvare quanto registrato.
- Pubblicata con GitHub Pages dal branch `main` (cartella radice). Nessun backend, nessun dato inviato altrove.
