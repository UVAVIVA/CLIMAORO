# CLIMAORO

**Sistema di termoregolazione a zone open source**

CLIMAORO è un sistema completo per il controllo centralizzato del riscaldamento e raffrescamento in edifici con impianto a pavimento e pompa di calore, ma adattabile a tutte le tipologie. Progettato per essere replicabile, modulare e professionale.

---

**🇬🇧 [English version](https://UVAVIVA.github.io/CLIMAOROen/)**

---

## La storia di questo progetto

Ho iniziato questo progetto a marzo 2026. Non sapevo programmare. Non sapevo saldare. Non sapevo stampare in 3D. Avevo solo un problema da risolvere e la voglia di imparare.

Oggi, ad agosto 2026, il sistema raffresca 16 ore al giorno. I termostati funzionano. Il collettore comanda le valvole. La logica per l'inverno è pronta. Il sistema è già integrato con il fotovoltaico per ottimizzare i consumi estivi.

Non è un prodotto finito. È un progetto in evoluzione, costruito pezzo per pezzo, giorno per giorno. Ma ha già un'impronta professionale, ed è pensato per essere replicabile, strutturato e completo.

---

## Perché l'ho fatto

### Il problema dei cicli brevi

Ho un impianto a pavimento con pompa di calore on/off. In inverno, le zone piccole (un bagno, una cameretta) richiedono poca acqua. La pompa di calore va sempre alla stessa potenza: in due minuti raggiunge la temperatura di mandata e si spegne. Poi si riaccende dopo dieci minuti. Decine di cicli al giorno.

Consumo inutile. Usura. Inefficienza.

Volevo che la pompa si accendesse solo quando serve davvero, e che restasse accesa abbastanza a lungo da essere efficiente.

### La domotica deve avere senso

La maggior parte della domotica è uno spreco di denaro. Luci che si accendono da sole, tapparelle automatiche, assistenti vocali: sono comodi, ma non ripagano l'investimento.

Il riscaldamento e il raffrescamento sono diversi. Sono il sessanta-settanta per cento della bolletta. Ottimizzarli ha un ritorno economico reale.

### I termostati commerciali: costosi e chiusi

Un termostato WiFi di marca costa da cento euro in su, fino a superare i duecentocinquanta. Il mio termostato costa meno di quindici euro di componenti.

Ma il problema non è solo il costo. I sistemi commerciali sono spesso chiusi: dipendono da cloud proprietari, non si integrano liberamente con Home Assistant, non possono essere modificati o riparati. Con il fai-da-te hai personalizzazione reale: puoi aggiungere funzionalità che prima non esistevano, adattare il sistema alle tue esigenze, e avere il controllo completo del tuo impianto.

### Una soluzione che sfrutta ESP-NOW

ESP-NOW è un protocollo di comunicazione diretta peer-to-peer di Espressif. Permette ai dispositivi ESP32 di comunicare tra loro senza passare da un router WiFi. Nel mio sistema i termostati parlano con il collettore via ESP-NOW come canale primario o di fallback. Il WiFi si usa per la comunicazione con Home Assistant, ma se il WiFi cade il sistema continua a funzionare.

Vantaggi: indipendenza dal router, bassa latenza, comunicazione cifrata. E i dispositivi possono fare da ripetitori per estendere la rete dove il segnale non arriva. Una caratteristica che molti progetti trascurano, ma che rende il sistema affidabile e robusto.

### Costruire è la vera soddisfazione

Potevo comprare termostati commerciali e un sistema di controllo. Ma non avrei imparato nulla. Non avrei avuto il controllo completo. Non avrei avuto la soddisfazione di costruire qualcosa che prima non esisteva.

Costruire è il motivo per cui questo progetto esiste.

---

**Costruito con passione, dal nulla.**