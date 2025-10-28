# Programming the OS-DCC-Decoder

This document provides a complete step-by-step guide on how to program the OS-DCC-Decoder using an Arduino as ISP programmer.

---

## Step 1 — Requirements

Before starting, make sure you have:
- An **Arduino Uno or Nano** (used as the programmer)
- The **OS-DCC-Decoder board**
- A set of **dupont wires** for the ICSP connection
- A USB cable for the Arduino
- Installed **Arduino IDE** on your computer

![plaatje_1.png]

---

## Step 2 — Make the Connections

Connect the Arduino to the OS-DCC-Decoder board using the ICSP header pins.

| Arduino Pin | OS-DCC-Decoder Pin |
|--------------|--------------------|
| 10 | RESET |
| 11 | MOSI |
| 12 | MISO |
| 13 | SCK |
| 5V | VCC |
| GND | GND |

Make sure the orientation of the ICSP header matches the markings on the board.

![plaatje_2.png]

---

## Step 3 — Flash the ArduinoISP Program

Open **Arduino IDE**, select your Arduino model under **Tools → Board**, and the correct COM port.  
Then go to **File → Examples → 11.ArduinoISP → ArduinoISP** and upload it to your Arduino.

![plaatje_3.png]

---

## Step 4 — Set Up the Programmer

Once the ArduinoISP sketch is uploaded, the Arduino now acts as an ISP programmer.

To verify communication, open **Tools → Programmer → Arduino as ISP**.

![plaatje_4.png]

---

## Step 5 — Connect the OS-DCC-Decoder

Ensure the OS-DCC-Decoder is powered through the ICSP 5 V pin.  
Double-check all connections before continuing.

![plaatje_5.png]

---

## Step 6 — Burn the Bootloader (optional)

If the microcontroller is new or unprogrammed, burn the bootloader first.  
In Arduino IDE, go to **Tools → Burn Bootloader**.  
This step initializes the fuses and clock configuration.

![plaatje_6.png]

---

## Step 7 — Load the OS-DCC Firmware

Now open the decoder firmware sketch in the Arduino IDE.  
Ensure the correct board type and clock speed are selected in the Tools menu.

![plaatje_7.png]

---

## Step 8 — Upload Using the Programmer

Choose **Sketch → Upload Using Programmer** instead of the regular upload button.  
This writes the firmware directly to the microcontroller without using a serial bootloader.

![plaatje_8.png]

---

## Step 9 — Check the Serial Monitor (optional)

Once flashed, open the Serial Monitor at **9600 baud** to check for diagnostic messages from the decoder.

![plaatje_9.png]

---

## Step 10 — Test the Decoder

Connect the decoder to a DCC track and verify basic functionality.  
Ensure that the LED indicators and servo outputs respond correctly to DCC commands.

![plaatje_10.png]

---

## Step 11 — Adjust Configuration

The OS-DCC-Decoder may allow basic configuration via CVs or jumpers.  
Consult your decoder’s manual for the specific settings.

![plaatje_11.png]

---

## Step 12 — Common Issues

| Symptom | Possible Cause | Solution |
|----------|----------------|----------|
| Upload fails | Wrong COM port | Re-select the correct port |
| "Invalid device signature" | Wrong wiring | Double-check ICSP connections |
| No LED activity | Power missing | Check 5 V line |

![plaatje_12.png]

---

## Step 13 — Verify Programming Result

When the upload completes successfully, you will see a confirmation message in the IDE.

![plaatje_13.png]

---

## Step 14 — Disconnect the Programmer

After flashing, disconnect the Arduino from the decoder.  
Your OS-DCC-Decoder is now ready for standalone use.

![plaatje_14.png]

---

## Step 15 — Optional: Program Multiple Boards

You can use the same ArduinoISP setup to flash multiple decoders.  
Just connect each board to the ICSP header in turn.

![plaatje_15.png]

---

## Step 16 — Testing Multiple Boards

If programming multiple decoders, test each one after flashing to ensure consistent behavior.

![plaatje_16.png]

---

## Step 17 — Troubleshooting Upload Errors

If upload errors persist, try lowering the SPI clock speed or reconnecting the ICSP cable.

![plaatje_17.png]

---

## Step 18 — Alternative: Use USBasp

A dedicated USBasp programmer can also be used instead of ArduinoISP.  
Select **USBasp** under Tools → Programmer and upload the firmware normally.

![plaatje_18.png]

---

## Step 19 — Arduino as Bootloader Loader

The ArduinoISP can also burn bootloaders for other microcontrollers, not just the OS-DCC-Decoder.

![plaatje_19.png]

---

## Step 20 — Final Verification

Recheck the firmware version and configuration once more before installation.

![plaatje_20.png]

---

## Step 21 — Finished

Your OS-DCC-Decoder is now successfully programmed and ready for use in your layout.

![plaatje_21.png]

---

*End of document.*
