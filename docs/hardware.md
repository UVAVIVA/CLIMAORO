# Hardware

## Note generali sui pin

I pin indicati negli schemi e nelle tabelle sono esempi basati sulle configurazioni attuali. Ogni installazione può variare in base al modello di scheda utilizzato (ESP32-S3, ESP32-C6, ESP32-C3, formato mini o standard). I pin vanno adattati al proprio hardware e alle proprie esigenze.

## Il collettore

### Microcontrollori compatibili

| Chip | Note |
|------|------|
| **ESP32-C6** | Utilizzato attualmente, supporto WiFi + ESP-NOW |
| **ESP32-S3** | Alternativa valida, maggior potenza di calcolo |
| **ESP32-C3** | Compatibile, minori risorse ma sufficiente |

### Componenti e funzioni

| Componente | Quantità | Funzione |
|------------|----------|----------|
| Microcontrollore | 1 | ESP32-C6/S3/C3 con WiFi + ESP-NOW |
| Relè | 4+ | Comando valvole zone |
| Relè | 1 | Comando circolatore |
| Optoisolatori | 4+ | Feedback valvole |
| LED | 1 | Segnalazione stato |

<img src="../images/collettore/1.jpg" alt="Collettore 1" width="32%"> <img src="../images/collettore/2.jpg" alt="Collettore 2" width="32%"> <img src="../images/collettore/3.jpg" alt="Collettore 3" width="32%">

### Logica di funzionamento

| Funzione | Descrizione |
|----------|-------------|
| Ricezione comandi | Riceve comandi dai termostati via ESP-NOW o WiFi |
| Conferme | Invia conferme ai termostati |
| Allarmi | Invia allarmi in caso di anomalie |
| Gestione circolatore | Logiche di temporizzazione personalizzabili |
| Timeout sicurezza | Valuta lo spegnimento dopo tempo prestabilito |
| Controllo coerenza | Verifica perpetua tra stato richiesto e stato effettivo |
| Feedback | Lettura optoisolatori per verifica stato valvole |

## I termostati

### Microcontrollori compatibili

| Chip | Note |
|------|------|
| **ESP32-S3** | Consigliato per modelli con display (es. formato Zero mini) |
| **ESP32-C6** | Per modelli senza display o con funzionalità base |
| **ESP32-C3** | Per modelli compatti o ripetitori |

### Modelli e installazioni

| Modello | Installazione | Funzione specifica |
|---------|---------------|-------------------|
| **Mobile** | Presa elettrica | Plug-and-play, soluzione standard |
| **Interno 503** | Dentro scatola 503 | Interfaccia utente locale |
| **Affiancato 503** | Affiancato a scatola 503 | Modulo compatto, controlli essenziali |
| **Ripetitore** | Affiancato o dentro 503 | Estensione rete ESP-NOW |
| **Pannello** | Affiancato o dentro 503 | Controllo centralizzato, menu completo |

<img src="../images/termostati/1.jpg" alt="Termostato 1" width="32%"> <img src="../images/termostati/2.jpg" alt="Termostato 2" width="32%"> <img src="../images/termostati/3.jpg" alt="Termostato 3" width="32%">

### Caratteristiche comuni

| Componente | Funzione |
|------------|----------|
| Microcontrollore | Elaborazione e comunicazione (S3, C6 o C3) |
| Sensore | Rilevamento temperatura e umidità ambiente |
| LED | Segnalazioni di stato |
| Comunicazione | WiFi + ESP-NOW (primario e fallback) |

### Case stampa 3D termostato mobile

Il case del termostato mobile è disponibile per la stampa 3D.

- **File:** [termostato-ovale-19-c6.3mf](files/termostato-ovale-19-c6.3mf)
- **Materiale consigliato:** PETG
- **Nota:** il file può essere aperto solo con **OrcaSlicer** o **Flash Studio**
- **Tutorial:** [Guida completa al montaggio](montaggio.md)
