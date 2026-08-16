# Montaggio del termostato

Costruzione del termostato CLIMAORO: una scheda **ESP32** alimentata da un
caricatore USB riciclato, collegata a un sensore di temperatura/umidità **SHT40**
e inserita nel **case stampato in 3D** al posto del vecchio termostato a muro.

> ⚠️ **PERICOLO – TENSIONE DI RETE (230V).** Questo montaggio lavora collegato
> alla rete elettrica: il contatto con la tensione può provocare scosse
> elettriche pericolose. Prima di qualsiasi intervento **stacca la corrente**.
> Non toccare i componenti interni con il dispositivo alimentato. **Se non hai
> esperienza con l'elettricità, fai eseguire l'installazione da un elettricista
> qualificato.**

---

## Stampa 3D del case

Il case del termostato si stampa in 3D. Il modello è lo stesso usato per il
termostato mobile:

- **File:** [termostato-ovale-19-c6.3mf](files/termostato-ovale-19-c6.3mf)
- **Materiale consigliato:** PETG
- **Nota:** il file può essere aperto solo con **OrcaSlicer** o **Flash Studio**

> ⚠️ **Disclaimer:** il modello 3D è fornito così com'è, a scopo educativo e
> sperimentale. Le tolleranze possono variare in base a stampante, materiale e
> calibrazione. Non certificato per uso produttivo.

---

## Fasi di montaggio

### Materiali necessari

| Materiale                         | Uso                          |
| --------------------------------- | ---------------------------- |
| ESP32 (C3 o C6)                   | Cervello del termostato      |
| Caricatore USB per cellulare (5V) | Alimentazione (riciclato)    |
| Sensore SHT40 (temp/umidità)      | Misura della temperatura     |
| Case stampato in 3D               | Alloggia PCB, ESP32 e sensore |
| Cacciavite piccolo                | Aprire il caricatore         |
| Saldatore + stagno                | Collegamenti elettrici       |
| Filo (rosso, bianco, verde, giallo, nero) | Cablaggio            |

<img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/1.jpg" alt="Montaggio termostato 1" width="32%"> <img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/2.jpg" alt="Montaggio termostato 2" width="32%"> <img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/3.jpg" alt="Montaggio termostato 3" width="32%">

### 1. Aprire il caricatore

Con un piccolo cacciavite apri l'involucro del caricatore USB del cellulare.
Dal caricatore ti servono due parti:

- i **due spinotti metallici** (i contatti maschi che si infilano nella presa a
  muro, dove passano i 230V);
- il **PCB** (la scheda interna), da cui prenderai i **5V** per alimentare
  l'ESP32.

L'involucro di plastica del caricatore invece non viene usato: al suo posto i
componenti saranno alloggiati nel case stampato in 3D.

### 2. Saldare i collegamenti

A saldature complete il circuito sarà questo:

```
                    ┌─────────────────┐
 CARICATORE USB ───>│    ESP32        │
   (5V dal PCB)     │                 │
   VCC (rosso) ─────> 5V / VIN        │
   GND (bianco) ────> GND             │
                    │                 │
 SENSORE SHT40 ────>│                 │
   VCC (giallo) ────> 3V3             │
   GND (verde) ─────> GND             │
   SDA (nero) ──────> SDA (pin i2c)   │
   SCL (rosso) ─────> SCL (pin i2c)   │
                    └─────────────────┘
```

Sul PCB del caricatore salda il filo **VCC (rosso)** e il filo **GND (bianco)**.
Salda anche lo **spinotto elettrico** che farà presa nella base del termostato a
muro (porta l'alimentazione 230V al caricatore).

Sull'ESP32 salda i due fili del caricatore (alimentazione) e i quattro fili del
sensore:

- **GND (verde)** → pin GND
- **VCC (giallo)** → pin 3V3
- **SDA (nero)** → pin SDA
- **SCL (rosso)** → pin SCL

> **Nota:** i pin SDA/SCL dipendono dal modello di ESP32 e sono definiti nel
> file di configurazione ESPHome (`i2c_sda` / `i2c_scl`):
> - ESP32-C6 → SDA 20, SCL 14
> - ESP32-C3 → SDA 0, SCL 1

Verifica sempre i pin nel tuo file YAML prima di saldare.

<img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/4.jpg" alt="Montaggio termostato 4" width="32%"> <img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/5.jpg" alt="Montaggio termostato 5" width="32%"> <img src="https://raw.githubusercontent.com/UVAVIVA/CLIMAORO/main/docs/images/montaggio/6.jpg" alt="Montaggio termostato 6" width="32%">

### 3. Inserire i componenti nel case 3D

Infila in quest'ordine nel case stampato in 3D, dove gli spinotti funzioneranno
da chiusura:

1. il **fascio di fili** (i cavi verso l'esterno)
2. la **ESP32**
3. il **PCB del caricatore** con gli spinotti saldati, che chiuderanno la spina
   del termostato

### 4. Sistemare l'ESP32 e il sensore

Inserisci la ESP32 nell'alloggiamento del case e instrada i fili del sensore
verso la parte inferiore.

### 5. Chiudere il coperchio

Inserisci il coperchio del termostato con la **gamba più snella** dalla parte
opposta all'ESP32: quello spazio è il più ridotto, mentre l'altra gamba entra a
fatica. Chiudi il tutto con due viti. Collega il sensore ai quattro fili e
infilalo nel suo alloggiamento dedicato.

---

## Verifica finale

1. Ricollega la corrente.
2. Il termostato dovrebbe apparire online in Home Assistant (via ESPHome/API).
3. Controlla che il sensore pubblichi temperatura e umidità.
4. Se non compare: ricontrolla le saldature (soprattutto SDA/SCL e le
   alimentazioni) e la tensione del caricatore.

---

## Note

- **⚠️ Sicurezza:** il montaggio contiene tensione di rete (230V) all'interno
  del caricatore. **Lavora sempre a corrente staccata**, usa materiali isolati
  e verifica i collegamenti prima di riattaccare la corrente. Non esporre il
  dispositivo a umidità o contatti accidentali.
- **Recupero:** il caricatore USB è un componente riciclato: basta che eroghi
  5V stabili e almeno ~1A.
- **Riferimento:** questo tutorial è parte della documentazione ufficiale
  [CLIMAORO su GitHub](https://github.com/UVAVIVA/CLIMAORO).
