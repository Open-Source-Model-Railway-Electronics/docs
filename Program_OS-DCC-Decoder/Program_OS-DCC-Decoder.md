# Flashing an OS Decoder with firmware

## Prelude
Programming any OS decoder has to be done via a method which is called **In Circuit Serial Programming** (ICSP for short). The Arduino website has a very elaborate explanation how that works and how you can do this. I have a shorter tutorial however. It does involve using a computer.

One final note. This page was originally written for the first decoder named **OSSD**, but the process is the same for all OS decoders and every other Open-Source design that require firmware.

---

## Step 1: Download the necessary files
The firmware that is going to be flashed on the OS-decoder is a so-called binary file. You can recognize them by the `.hex` extension. All officially released binaries are found here:  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

To obtain the software, download the entire repository by clicking the green **Code** button and choosing **Download ZIP**.

![Download repository](plaatje_1.png)

---

## Make the connections
An OS-decoder cannot be connected to a computer directly. In order to do this we need to use an **Arduino** board.

First make the connections between Arduino and decoder. **Make sure that the Arduino is not plugged into the computer while you connect the wires.**

Every decoder has an **ICSP** connector for programming. You may solder a pin header on it, or use **dupont** wires. Alternatively you can purchase a **pogopin clamp**, which allows programming without soldering.

Make the following 6 connections between decoder (**OSSD**) and Arduino UNO:

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

An early OSSD model connected to the Arduino programmer. When the Arduino is connected to the decoder you can plug it into the computer via a USB cable.

![OSSD connected](plaatje_4.png)

If you intend to do this often, a **1×6 pogo pin clamp** (0.1″ / 2.54 mm pitch) is convenient. It presses conical spring-loaded pins against the ICSP connector, so you never have to solder a header.

A fully assembled OSSD programmed via pogo pin clamp.

![Pogo pin clamp](plaatje_5.png)

---

## Prepare the programmer
The next step is to turn the Arduino board into a programmer by flashing Arduino’s **ArduinoISP** firmware into it.  
The easiest way is simply dragging the file `ArduinoISP.hex` onto `UPLOAD_PROGRAM.bat`.

The batch file automatically detects a connected Arduino via USB and flashes the hex file into it, turning the board into a ready-to-use ICSP programmer.

![Uploading ArduinoISP](plaatje_6.png)

Once the Arduino is programmed, insert a **10 µF (or larger)** capacitor between **RESET (+)** and **GND (–)** on the Arduino.  
This prevents the Arduino from resetting when it is later used to program the decoder.

After that, your Arduino programmer is ready to use.

---

## Flash the Decoder
Flashing the decoder works the same way.  
Simply drag the desired **decoder `.hex` file** onto **`UPLOAD_PROGRAM.bat`**.

If successful, you’ll see a progress window similar to the previous step.

![Flashing decoder](plaatje_12.png)

> **Note:** Occasionally the upload may fail or the board may appear unresponsive.  
> Just repeat the process until the flash completes successfully.

![Upload retry](plaatje_13.png)

---

### End of document
