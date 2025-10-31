# Firmware flashen op een OS‑decoder

## Voorwoord
Het programmeren van een OS‑decoder gebeurt via **In Circuit Serial Programming** (**ICSP**). Op de Arduino‑website staat een uitgebreide uitleg; hieronder een kortere handleiding. Een computer is nodig.

Let op: deze pagina is oorspronkelijk geschreven voor de eerste decoder **OSSD**, maar de werkwijze is hetzelfde voor alle OS‑decoders en andere open‑source ontwerpen die firmware vereisen.

---

## Stap 1: Benodigde bestanden downloaden
De firmware die je flasht is een binaire file met de extensie **`.hex`**. Alle officiële releases vind je hier:  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

Download het complete repository via de groene **Code**‑knop → **Download ZIP**.

![Repository downloaden](plaatje_1.png)

---

## Sluit alles aan
Een OS‑decoder kan niet direct aan de computer. We gebruiken een **Arduino**‑board.

Maak eerst de verbindingen tussen Arduino en decoder. **Zorg dat de Arduino niet op de computer is aangesloten tijdens het bedraden.**

Elke decoder heeft een **ICSP**‑connector. Solderen van een pinheader kan, of gebruik **dupont**‑draden. Een **pogopin‑klem** werkt ook en voorkomt solderen.

Maak deze 6 verbindingen tussen decoder (**OSSD**) en Arduino UNO:

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

Een vroeg OSSD‑model aan de Arduino‑programmer. Als alles is aangesloten, kun je de Arduino met USB op de computer aansluiten.

![OSSD aangesloten](plaatje_4.png)

Ga je dit vaker doen? Overweeg een **1×6 pogopin‑klem** (0,1″ / 2,54 mm). Veerbelaste conische pinnen drukken op de ICSP‑connector; solderen is niet nodig.

Een volledig geassembleerde OSSD geprogrammeerd via pogopin‑klem.

![Pogopin‑klem](plaatje_5.png)

---

## ArduinoISP flashen
Vervolgens maken we van de Arduino een programmeerapparaat door **ArduinoISP** te flashen.  
De simpelste manier: sleep **`ArduinoISP.hex`** op **`UPLOAD_PROGRAM.bat`**.

Het batchbestand detecteert automatisch een via USB aangesloten Arduino en flasht het HEX‑bestand. Daarna is de Arduino een ICSP‑programmer.

![ArduinoISP uploaden](plaatje_6.png)

Plaats daarna een **condensator van 10 µF (of groter)** tussen **RESET (+)** en **GND (–)** op de Arduino.  
Dit voorkomt dat de Arduino reset tijdens het programmeren van de decoder.

![Condensator geplaatst](plaatje_10.png)

De Arduino‑programmer is nu klaar voor gebruik.

---

## De decoder flashen
Dit werkt hetzelfde:  
Sleep het gewenste **decoder‑`.hex`‑bestand** op **`UPLOAD_PROGRAM.bat`**.

Bij succes verschijnt een voortgangsvenster zoals bij de vorige stap.

![Decoder flashen](plaatje_12.png)

> **Let op:** Het uploaden kan soms mislukken of het board reageert niet.  
> Herhaal de handeling totdat het flashen slaagt.

![Upload opnieuw](plaatje_13.png)

---

### Einde van het document
