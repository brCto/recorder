# Registratore del Quaderno

Pagina singola (`index.html`) che registra l'audio di una lezione con trascrizione in diretta (Web Speech API, `it-IT`) e la rimanda al [Quaderno delle Lezioni](https://claude.ai/artifact/7TPQ5eFeinkV4uYiLA4EsH).

Esiste perché il frame degli artifact su claude.ai non riceve il permesso del microfono: questa pagina, aperta come pagina principale su un dominio proprio, lo può chiedere normalmente.

- Aperta dal Quaderno con `?lesson=<id>&title=…`, parla con la scheda che l'ha aperta via `postMessage` (segmenti in diretta, poi audio e trascrizione a fine registrazione).
- L'audio è salvato pezzo per pezzo in IndexedDB: se la scheda muore, al riavvio propone di inviare o salvare quanto registrato.
- Trascrizione sul dispositivo con Whisper (transformers.js, WebGPU se c'è): in diretta durante la registrazione, a finestre di ~15 s tagliate nei silenzi, con passaggio automatico dal riconoscimento del browser quando questo non produce testo (Android); la coda finisce anche dopo lo stop e il testo raggiunge il Quaderno come aggiornamento (`transcribed`). Su richiesta del Quaderno (`transcribe`) trascrive i file caricati lì, anche più file in sequenza con i tempi che proseguono.
- "Trascrivi una registrazione": scelta di uno o più file audio, trascrizione offline, testo da inviare o copiare.
- Pubblicata con GitHub Pages dal branch `main` (cartella radice). Nessun backend, nessun dato inviato altrove.
