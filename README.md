# Spazio Nerazzurro 2.0 — GitHub Pages

Pacchetto statico: GitHub Pages non esegue PHP. La pubblicazione avviene tramite GitHub Actions.

## Pubblicazione
1. Crea un repository `TUO-UTENTE.github.io` per pubblicare alla radice `https://TUO-UTENTE.github.io/`.
2. Carica il contenuto di questa cartella nel branch `main`.
3. In Settings → Pages → Build and deployment seleziona GitHub Actions.
4. In Settings → Actions → General abilita i permessi di scrittura per i workflow.
5. Sostituisci `TUO-UTENTE` con il tuo account/dominio in `index.html`, `robots.txt`, `scripts/generate_editorials.py` e `worker/wrangler.toml`.

## API sportive
1. Crea un Cloudflare Worker usando i file nella cartella `worker`.
2. Esegui `wrangler login`, poi `wrangler deploy`.
3. Imposta la chiave segreta con `wrangler secret put API_FOOTBALL_KEY`.
4. Imposta `ALLOWED_ORIGIN` sul dominio GitHub Pages effettivo e ridistribuisci.
5. Copia l'URL del Worker in `assets/config.js`, campo `sportsApi`.

Il Worker espone `/fixtures` e `/standings`. Team Inter: 505; Serie A: 135. Verifica che il tuo piano API-Football includa la competizione e la stagione richieste.

## Contenuti e aggiornamento
I CSV Google Sheets sono già configurati in `assets/config.js`. Le intestazioni riconosciute sono titolo/title, data/date, descrizione/description/sottotitolo, testo/contenuto e url/link. Il workflow genera le pagine editoriali e `sitemap.xml` a ogni push e con aggiornamento pianificato giornaliero.

Per un repository diverso da `TUO-UTENTE.github.io` o per un dominio personalizzato, aggiorna anche i percorsi base dei link. La pianificazione GitHub Actions può subire ritardi. Il pacchetto è pronto da configurare ma non è stato pubblicato o testato sul tuo account.
