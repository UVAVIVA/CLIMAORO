# Software

## Architettura

La logica di controllo è centralizzata e si integra con Home Assistant. I dispositivi (termostati e collettore) utilizzano firmware basato su ESPHome, che permette un'integrazione nativa con Home Assistant e una configurazione flessibile.

## Comunicazione

Il sistema utilizza due canali di comunicazione:

| Canale | Protocollo | Scopo |
|--------|------------|-------|
| Primario | WiFi + API ESPHome | Configurazione, telemetria, comandi da Home Assistant |
| Fallback | ESP-NOW | Comunicazione diretta termostati ↔ collettore (senza router) |

## Entità esposte in Home Assistant

| Entità | Tipo | Descrizione |
|--------|------|-------------|
| climate.*_climatizzazione | climate | Termostato |
| sensor.*_temperatura_reale | sensor | Temperatura ambiente |
| sensor.*_umidita_reale | sensor | Umidità ambiente |
| sensor.*_stato_sistema | sensor | Stato operativo |
| sensor.*_ultimo_errore | sensor | Ultimo errore rilevato |
| sensor.*_cronologia_errori | sensor | Storico errori |
| 
umber.*_temperatura_salvata | 
umber | Setpoint di riferimento |
| 
umber.*_soglia_umidita | 
umber | Soglia per blocco funzionamento |
| switch.*_modalita_controllata | switch | Abilitazione controllo centralizzato |
| utton.*_rinnovo_modalita | utton | Rinnovo timer controllo centralizzato |
| utton.*_reset_allarme_collettore | utton | Reset allarme collettore |
| utton.*_reset_allarme_circolatore | utton | Reset allarme circolatore |
| utton.*_reset_errori | utton | Reset errori |
| light.*_led_stato | light | LED di segnalazione |

## Logica di controllo centralizzata

### Parametri configurabili per zona

| Parametro | Tipo | Descrizione |
|-----------|------|-------------|
| Peso | Numero | Importanza della zona |
| Inclusione | Booleano | Inclusione/esclusione della zona |
| Delta guardia giorno | Numero | Temperatura di mantenimento (fascia giorno) |
| Delta guardia notte | Numero | Temperatura di mantenimento (fascia notte) |
| Delta lavoro giorno | Numero | Temperatura di funzionamento (fascia giorno) |
| Delta lavoro notte | Numero | Temperatura di funzionamento (fascia notte) |
| Temperatura salvata | Numero | Setpoint di riferimento |
| Soglia pesi | Numero | Soglia di attivazione collettiva |

### Flusso decisionale

1. **Raccolta dati:** temperatura reale, setpoint, azione, modalità per ogni zona
2. **Calcolo domanda:** per ogni zona, guardia = setpoint - delta_guardia; se temp <= guardia - 0.5 → richiede calore; somma pesi
3. **Priorità:** zone già in funzione hanno priorità
4. **Decisione collettiva:** se somma_pesi >= soglia_pesi → attiva tutte
5. **Emergenza individuale:** se temp <= guardia - 0.4 → attiva singola zona
6. **Esecuzione:** imposta setpoint di lavoro per le zone da attivare, setpoint di guardia per le zone da disattivare

## Segnalazioni LED

Le segnalazioni variano a seconda della configurazione e possono essere personalizzate. A titolo di esempio:

| Stato | Segnalazione tipica |
|-------|---------------------|
| Funzionamento attivo | Colore fisso |
| Standby | Colore fisso diverso |
| Problemi minori | Lampeggio lento |
| Errori gravi | Lampeggio rapido |
| Allarmi | Lampeggio specifico |

Le funzioni di segnalazione sono configurabili e adattabili alle proprie esigenze.

## File di configurazione

I file di configurazione ESPHome sono pubblici su GitHub nel repository [climaoro-components](https://github.com/UVAVIVA/climaoro-components).

| File | Link |
|------|------|
| Config principale termostato (esempio italiano) | [termostato_esempio.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/termostato_esempio.yaml) |
| Config principale termostato (esempio inglese) | [termostato_example.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/termostato_example.yaml) |
| Package termostato | [packages/termostato.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/packages/termostato.yaml) |
| Package termostato con display | [packages/termostato_display.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/packages/termostato_display.yaml) |
| Package collettore | [packages/collettore.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/packages/collettore.yaml) |
| Package zona | [packages/zona.yaml](https://raw.githubusercontent.com/UVAVIVA/climaoro-components/main/packages/zona.yaml) |

Il file `secrets.yaml` (chiavi WiFi e API) non viene pubblicato: va creato localmente per ogni installazione.
