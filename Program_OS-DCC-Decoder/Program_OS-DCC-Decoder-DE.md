# Flashen einer OS-Decoder‑Firmware

## Einleitung
Das Programmieren eines OS‑Decoders erfolgt per **In‑Circuit Serial Programming** (**ICSP**). Auf der Arduino‑Website gibt es eine ausführliche Erklärung; hier folgt eine kürzere Anleitung. Ein Computer ist erforderlich.

Hinweis: Diese Seite wurde ursprünglich für den ersten Decoder **OSSD** geschrieben, aber der Ablauf ist für alle OS‑Decoder und andere Open‑Source‑Designs mit Firmware identisch.

---

## Schritt 1: Notwendige Dateien herunterladen
Die zu flashende Firmware ist eine Binärdatei mit der Endung **`.hex`**. Alle offiziell veröffentlichten Binaries finden Sie hier:  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

Laden Sie das gesamte Repository herunter, indem Sie auf den grünen **Code**‑Button klicken und **Download ZIP** wählen.

![Repository herunterladen](plaatje_1.png)

---

## Verbindungen herstellen
Ein OS‑Decoder kann nicht direkt an den Computer angeschlossen werden. Dafür verwenden wir ein **Arduino**‑Board.

Stellen Sie zuerst die Verbindungen zwischen Arduino und Decoder her. **Der Arduino darf beim Verdrahten nicht mit dem Computer verbunden sein.**

Jeder Decoder besitzt einen **ICSP**‑Anschluss. Entweder löten Sie eine Stiftleiste an oder verwenden **Dupont**‑Leitungen. Alternativ eignet sich eine **Pogopin‑Klammer**, mit der Sie ohne Löten programmieren können.

Stellen Sie folgende 6 Verbindungen zwischen Decoder (**OSSD**) und Arduino UNO her:

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

Ein frühes OSSD‑Modell am Arduino‑Programmierer. Sobald der Arduino verbunden ist, können Sie ihn per USB mit dem Computer verbinden.

![OSSD verbunden](plaatje_4.png)

Wenn Sie häufiger programmieren, ist eine **1×6 Pogopin‑Klammer** (Raster 0,1″ / 2,54 mm) sehr praktisch. Federnde, konische Pins drücken auf den ICSP‑Anschluss – Löten entfällt.

Ein vollständig montierter OSSD, programmiert mit Pogopin‑Klammer.

![Pogopin‑Klammer](plaatje_5.png)

---

## ArduinoISP aufspielen
Als Nächstes verwandeln wir den Arduino in einen Programmer, indem wir Arduinos **ArduinoISP**‑Firmware aufspielen.  
Am einfachsten ziehen Sie die Datei **`ArduinoISP.hex`** auf **`UPLOAD_PROGRAM.bat`**.

Das Batch‑Skript erkennt den per USB verbundenen Arduino automatisch und flasht die HEX‑Datei – der Arduino ist danach ein einsatzbereiter ICSP‑Programmer.

![ArduinoISP hochladen](plaatje_6.png)

Sobald der Arduino programmiert ist, stecken Sie einen **Kondensator mit 10 µF (oder größer)** zwischen **RESET (+)** und **GND (–)** auf dem Arduino.  
Das verhindert, dass sich der Arduino beim Programmieren des Decoders zurücksetzt.

![Kondensator eingesetzt](plaatje_10.png)

Danach ist Ihr Arduino‑Programmierer einsatzbereit.

---

## Den Decoder flashen
Das Flashen des Decoders funktioniert genauso:  
Ziehen Sie die gewünschte **Decoder‑`.hex`‑Datei** auf **`UPLOAD_PROGRAM.bat`**.

Bei Erfolg sehen Sie einen Fortschrittsdialog ähnlich wie zuvor.

![Decoder flashen](plaatje_12.png)

> **Hinweis:** Gelegentlich kann der Upload fehlschlagen oder das Board reagiert nicht.  
> Wiederholen Sie den Vorgang einfach, bis das Flashen erfolgreich ist.

![Upload erneut](plaatje_13.png)

---

### Ende des Dokuments
