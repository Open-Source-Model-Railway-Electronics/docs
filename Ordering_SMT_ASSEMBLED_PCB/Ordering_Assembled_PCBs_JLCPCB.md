# Ordering Assembled PCBs from JLCPCB

This document explains how to order **assembled PCBs** (with components already soldered) from JLCPCB using the online SMT assembly service.  
It includes all steps from uploading the Gerber files, adding the BOM and CPL, to selecting parts and confirming production.

---

## Step 1 — Visit the Website

Go to [JLCPCB.com](https://jlcpcb.com) and click **“SMT Assembly”**.  
You can either log in or continue as a guest to start the process.

![Figure 1: JLCPCB main page with SMT Assembly option](plaatje_1.png)

---

## Step 2 — Upload Your Gerber Files

Click **“Add your Gerber file”** and select your design ZIP file.  
This ZIP contains all manufacturing layers, including copper, drill, and mask data.

The preview will load after a few seconds, showing both sides of your PCB.

![Figure 2: Uploading Gerber files and seeing the board preview](plaatje_2.png)

---

## Step 3 — Configure Board Options

On the configuration screen, you can choose the PCB parameters:  
- Quantity (default: 5 pieces)  
- Color (green, blue, red, black, white, purple)  
- Thickness (1.6 mm by default)  
- Copper weight (1 oz typical)  
- Surface finish (HASL or ENIG)  

If you are ordering an **assembled board**, keep the default copper and surface settings unless your project specifies otherwise.

![Figure 3: PCB configuration settings](plaatje_3.png)

---

## Step 4 — Select “SMT Assembly”

Enable the **SMT Assembly** option below the preview.  
Choose whether the assembly should be **on the top**, **bottom**, or **both sides** of the board.  
Most projects only use **top-side assembly**.

![Figure 4: Enabling SMT Assembly and choosing sides](plaatje_4.png)

---

## Step 5 — Upload the BOM and CPL Files

To assemble your board, JLCPCB needs two extra files:  
1. **BOM (Bill of Materials)** — list of all parts with reference designators, values, and part numbers.  
2. **CPL (Component Placement List)** — the position (X/Y) and rotation of each part on the board.

Upload both files when prompted.  
They are usually provided in your project’s release archive or repository.

![Figure 5: Uploading BOM and CPL files for assembly](plaatje_5.png)

---

## Step 6 — Verify Component Placement

After uploading the BOM and CPL, a visual tool opens showing the component positions.  
Each component will be marked on the board.

Zoom in and check that every component is placed correctly and matches the silk screen.  
If something looks wrong (rotated 90° or mirrored), fix it in your CAD tool before re-uploading.

![Figure 6: Visual verification of placed components](plaatje_6.png)

---

## Step 7 — Select Components

Next, the system matches your BOM with JLCPCB’s component library (LCSC).  
You can choose between:
- **Basic parts** (always in stock, cheap)
- **Extended parts** (special or less common)

Click **“Confirm”** once all parts are correctly matched.

![Figure 7: Selecting components from the JLCPCB/LCSC library](plaatje_7.png)

---

## Step 8 — Confirm the Assembly

A summary will appear showing your part costs, PCB costs, and total price.  
Review all details carefully before confirming.

Check that:
- The number of PCBs is correct.  
- The side to assemble (Top/Bottom) is correct.  
- All components are listed and available.  

![Figure 8: Assembly confirmation summary](plaatje_8.png)

---

## Step 9 — Add to Cart

Once satisfied, click **“Save to Cart.”**  
This stores the entire configuration, including your Gerbers, BOM, and CPL, for later reorders.

You can add more designs before proceeding to checkout.

![Figure 9: Cart with assembled PCB order](plaatje_9.png)

---

## Step 10 — Checkout and Payment

Proceed to checkout.  
Choose your **shipping method**, fill in your **address**, and complete payment via **PayPal** or **credit card**.

Production typically takes **3–5 business days** for assembly, plus shipping time.

![Figure 10: Checkout screen with shipping and cost details](plaatje_10.png)

---

## Step 11 — Receive Your Boards

Once your assembled PCBs arrive, inspect the solder joints, verify orientation of ICs, and test functionality.  
You now have a professionally manufactured and assembled circuit board — ready to use.

![Figure 11: Finished assembled PCBs from JLCPCB](plaatje_11.png)

---

### Notes

- Use the same Gerber, BOM, and CPL naming conventions for future orders.  
- You can reorder any previous design from your JLCPCB account dashboard.  
- The online viewer is accurate — if it looks correct there, the boards will match in real life.  

---

*End of document.*
