# Changelog

Tutte le modifiche rilevanti a questo modulo sono documentate in questo file.

Il formato è basato su [Keep a Changelog](https://keepachangelog.com/it/1.1.0/)
e questo progetto aderisce al [Semantic Versioning](https://semver.org/lang/it/).

## [1.0.0] - 2026-11-03

### Added
- **Storico dei prezzi** (`threecommerce_omnibus_price_history`): una riga per ogni variazione del prezzo effettivo di un
  prodotto in un sito web, letto dall'indice prezzi (gruppo "NOT LOGGED IN": prezzo speciale con date e regole catalogo già applicati).
  Registrazione al salvataggio del prodotto, dal cron orario (`3comm_omnibus_snapshot`) e dal comando
  `bin/magento threecommerce:omnibus:snapshot`.
- **Prezzo più basso precedente** (art. 17-bis Codice del Consumo, D.Lgs. 26/2023): sui prodotti in sconto compare il prezzo
  più basso dei N giorni (30) precedenti l'applicazione dello sconto. Gli sconti progressivi (100 → 80 → 70) restano riferiti
  al prezzo prima della prima riduzione. Nessun dato inventato: senza storico precedente lo sconto non mostra nulla.
- Configurazione in *Negozi → Configurazione → Threecommerce Plugins → Omnibus* (per store view): attivo (spento di default),
  giorni, scheda prodotto, elenchi, testo con `{price}` e `{days}`, storico più breve, conservazione dello storico.
- Nota nella scheda prodotto (Luma/Blank e Hyvä, con template dedicato) e, a scelta, negli elenchi categoria/ricerca.
- Svuotamento della cache dei prodotti il cui prezzo registrato cambia; pulizia dello storico oltre la conservazione
  (mantiene sempre il prezzo in vigore a inizio periodo).
