# Flashear el firmware de un decodificador OS

## Preámbulo
La programación de un decodificador OS se realiza mediante **In Circuit Serial Programming** (**ICSP**). En la web de Arduino hay una explicación detallada; aquí va una guía más breve. Es necesario un ordenador.

Nota: esta página se escribió originalmente para el primer decodificador **OSSD**, pero el proceso es el mismo para todos los decodificadores OS y otros diseños de código abierto que requieran firmware.

---

## Paso 1: Descargar los archivos necesarios
El firmware a flashear es un archivo binario con extensión **`.hex`**. Todas las versiones oficiales están aquí:  
`https://github.com/Open-Source-Model-Railway-Electronics/OS-software-tool`

Descargue el repositorio completo haciendo clic en el botón verde **Code** y eligiendo **Download ZIP**.

![Descargar repositorio](plaatje_1.png)

---

## Realizar las conexiones
Un decodificador OS no puede conectarse directamente al ordenador. Usaremos una placa **Arduino**.

Primero haga las conexiones entre Arduino y decodificador. **Asegúrese de que el Arduino no esté conectado al ordenador mientras cablea.**

Cada decodificador tiene un conector **ICSP** para programar. Puede soldar un header o usar cables **Dupont**. Alternativamente, use una **pinza de pogo‑pins** para programar sin soldar.

Haga las siguientes 6 conexiones entre el decodificador (**OSSD**) y un Arduino UNO:

| OSSD (ICSP) | Arduino (UNO) |
|--------------|---------------|
| 5 V   | 5 V   |
| GND   | GND   |
| SCK   | D13   |
| MISO  | D12   |
| MOSI  | D11   |
| RESET | D10   |

Un modelo OSSD temprano conectado al programador Arduino. Cuando esté conectado, enchufe el Arduino al ordenador por USB.

![OSSD conectado](plaatje_4.png)

Si va a hacerlo a menudo, una **pinza de pogo 1×6** (paso 0,1″ / 2,54 mm) es muy cómoda. Sus pines cónicos con muelle presionan sobre el conector ICSP, sin soldadura.

Un OSSD completamente montado, programado con pinza de pogo.

![Pinza de pogo](plaatje_5.png)

---

## Cargar ArduinoISP
Ahora convertimos el Arduino en programador cargando el firmware **ArduinoISP**.  
El modo más sencillo es arrastrar **`ArduinoISP.hex`** sobre **`UPLOAD_PROGRAM.bat`**.

El script por lotes detecta automáticamente el Arduino conectado por USB y flashea el archivo HEX, dejando la placa lista como programador ICSP.

![Cargando ArduinoISP](plaatje_6.png)

Una vez programado el Arduino, inserte un **condensador de 10 µF (o mayor)** entre **RESET (+)** y **GND (–)** en el Arduino.  
Esto evita que el Arduino se reinicie durante la programación del decodificador.

![Condensador añadido](plaatje_10.png)

El programador está listo.

---

## Flashear el decodificador
El procedimiento es el mismo:  
Arrastre el **archivo `.hex` del decodificador** sobre **`UPLOAD_PROGRAM.bat`**.

Si todo va bien, verá una ventana de progreso similar a la anterior.

![Flasheando decodificador](plaatje_12.png)

> **Nota:** A veces la carga falla o la placa no responde.  
> Repita el proceso hasta que se complete correctamente.

![Reintento de subida](plaatje_13.png)

---

### Fin del documento
