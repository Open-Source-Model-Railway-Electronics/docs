# Flash della firmware su un decoder OS

## Introduzione
La programmazione di un decoder OS avviene tramite **In Circuit Serial Programming** (**ICSP**). Sul sito Arduino trovi una spiegazione completa; qui segue una guida più breve. È richiesto un computer.

Nota: questa pagina è stata scritta originariamente per il primo decoder **OSSD**, ma la procedura è identica per tutti i decoder OS e altri progetti open‑source che richiedono firmware.

---

## Passo 1: Scaricare i file necessari
Il firmware da flashare è un file binario con estensione **`.hex`**. Tutti i rilasci ufficiali si trovano qui:  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

Per ottenere i file, scarica l’intero repository cliccando sul pulsante verde **Code** e scegliendo **Download ZIP**.

![Scarica repository](plaatje_1.png)

---

## Effettuare i collegamenti
Un decoder OS non può essere collegato direttamente al computer. Usiamo una scheda **Arduino**.

Effettua prima i collegamenti tra Arduino e decoder. **Assicurati che l’Arduino non sia collegato al computer mentre effettui il cablaggio.**

Ogni decoder ha un connettore **ICSP** per la programmazione. Puoi saldare un header oppure usare cavi **dupont**. In alternativa, utilizza una **pinza a pogo‑pin** per programmare senza saldatura.

Esegui i seguenti 6 collegamenti tra il decoder (**OSSD**) e un Arduino UNO:

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

Un primo modello OSSD collegato al programmatore Arduino. Quando è collegato, puoi connettere l’Arduino al computer tramite USB.

![OSSD collegato](plaatje_4.png)

Se prevedi di farlo spesso, una **pinza a pogo 1×6** (passo 0,1″ / 2,54 mm) è molto comoda: i pin con molla premono sul connettore ICSP, senza bisogno di saldare.

Un OSSD completamente assemblato programmato con pinza a pogo.

![Pinza a pogo](plaatje_5.png)

---

## Caricare ArduinoISP
Il passo successivo è trasformare l’Arduino in un programmatore caricando il firmware **ArduinoISP**.  
Il modo più semplice è trascinare **`ArduinoISP.hex`** su **`UPLOAD_PROGRAM.bat`**.

Lo script batch rileva automaticamente l’Arduino collegato via USB e carica il file HEX, rendendo la scheda un programmatore ICSP pronto all’uso.

![Caricamento ArduinoISP](plaatje_6.png)

Una volta programmato l’Arduino, inserisci un **condensatore da 10 µF (o maggiore)** tra **RESET (+)** e **GND (–)** sull’Arduino.  
Questo evita che l’Arduino si resetti durante la programmazione del decoder.

![Condensatore inserito](plaatje_10.png)

Il tuo programmatore è pronto.

---

## Flash del decoder
La procedura è la stessa:  
Trascina il **file `.hex` del decoder** su **`UPLOAD_PROGRAM.bat`**.

Se va a buon fine, vedrai una finestra di avanzamento simile a quella del passo precedente.

![Flash decoder](plaatje_12.png)

> **Nota:** Talvolta il caricamento può fallire o la scheda non risponde.  
> Ripeti l’operazione finché il flash non va a buon fine.

![Riprova upload](plaatje_13.png)

---

### Fine del documento
