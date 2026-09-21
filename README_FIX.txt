SPESA DI OGGI — FIX CONDIVISIONE

Questa versione:
- mantiene una sola lista condivisa in Firestore per il proprietario e i membri autorizzati;
- usa transazioni per quantità concorrenti tra smartphone;
- evita di aggiornare/ricreare un prodotto che nel frattempo è stato cancellato;
- verifica che un invito appartenga ancora al proprietario della lista prima di accettarlo;
- usa ID invito casuali invece di un hash corto prevedibile;
- separa la memoria locale per account;
- importa nel cloud i dati locali del proprietario solo quando il primo snapshot AUTOREVOLE del server della sua lista è vuoto.

Il file firestore.rules deve essere pubblicato nel progetto Firebase "spesa-di-oggi". Il semplice ZIP dell'app non può pubblicare automaticamente regole sul progetto Firebase.

FIX AGGIUNTIVA v7 — DOM-XSS (Snyk)
- Corretto il rendering delle liste prodotti in index.html.
- Rimossi i percorsi `localStorage -> products -> innerHTML` per todoList/boughtList.
- Le righe prodotto e il totale vengono ora costruiti con API DOM (`createElement`, `textContent`, `dataset`, `setAttribute`, `appendChild/replaceChildren`).
- Il dato prodotto non viene più inserito come HTML eseguibile nel rendering locale.
- Verifica sintattica JavaScript eseguita con Node.js: OK.
