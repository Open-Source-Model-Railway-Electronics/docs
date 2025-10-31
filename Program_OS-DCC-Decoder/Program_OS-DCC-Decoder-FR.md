# Flasher le firmware d’un décodeur OS

## Préambule
La programmation d’un décodeur OS se fait via **In Circuit Serial Programming** (**ICSP**). Le site Arduino propose une explication détaillée ; voici une version plus courte. Un ordinateur est nécessaire.

Remarque : cette page a été écrite à l’origine pour le premier décodeur **OSSD**, mais la procédure est identique pour tous les décodeurs OS et autres conceptions open‑source nécessitant un firmware.

---

## Étape 1 : Télécharger les fichiers nécessaires
Le firmware à flasher est un fichier binaire portant l’extension **`.hex`**. Toutes les versions officielles sont disponibles ici :  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

Pour obtenir les fichiers, téléchargez l’intégralité du dépôt : cliquez sur le bouton vert **Code** puis **Download ZIP**.

![Télécharger le dépôt](plaatje_1.png)

---

## Réaliser les connexions
Un décodeur OS ne peut pas être relié directement à l’ordinateur. Nous utilisons pour cela une carte **Arduino**.

Commencez par câbler l’Arduino au décodeur. **Assurez‑vous que l’Arduino n’est pas branché à l’ordinateur pendant le câblage.**

Chaque décodeur possède un connecteur **ICSP** pour la programmation. Soudez un connecteur ou utilisez des fils **Dupont**. Vous pouvez aussi utiliser une **pince à pogo‑pins**, pour programmer sans soudure.

Réalisez les 6 connexions suivantes entre le décodeur (**OSSD**) et un Arduino UNO :

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

Un ancien modèle OSSD raccordé à l’Arduino. Une fois câblé, branchez l’Arduino à l’ordinateur via USB.

![OSSD raccordé](plaatje_4.png)

Si vous programmez souvent, une **pince pogo 1×6** (pas 0,1″ / 2,54 mm) est très pratique : des broches coniques à ressort se posent sur le connecteur ICSP, sans soudure.

Un OSSD entièrement assemblé, programmé via pince pogo.

![Pince pogo](plaatje_5.png)

---

## Installer ArduinoISP
Transformez ensuite l’Arduino en programmateur en y flashant le firmware **ArduinoISP**.  
La méthode la plus simple consiste à faire glisser **`ArduinoISP.hex`** sur **`UPLOAD_PROGRAM.bat`**.

Le script batch détecte automatiquement l’Arduino connecté en USB et flashe le fichier HEX ; la carte devient un programmateur ICSP prêt à l’emploi.

![Téléversement d’ArduinoISP](plaatje_6.png)

Une fois l’Arduino programmé, insérez un **condensateur de 10 µF (ou plus)** entre **RESET (+)** et **GND (–)** sur l’Arduino.  
Cela évite que l’Arduino se réinitialise pendant la programmation du décodeur.

![Condensateur ajouté](plaatje_10.png)

Votre programmateur est prêt.

---

## Flasher le décodeur
La procédure est la même :  
Faites glisser le **fichier `.hex` du décodeur** sur **`UPLOAD_PROGRAM.bat`**.

En cas de succès, une fenêtre de progression similaire apparaît.

![Flash du décodeur](plaatje_12.png)

> **Note :** Il arrive que le téléversement échoue ou que la carte ne réponde pas.  
> Reprenez simplement l’opération jusqu’à réussite.

![Nouvel essai](plaatje_13.png)

---

### Fin du document
