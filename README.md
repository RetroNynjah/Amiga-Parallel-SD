# Retroninja Amiga Parallel SD

<img src="rev2\images\render.png" alt="Render" height="400"/><img src="rev2\images\render-top.png" alt="Render top" height="400"/><br/>

MicroSD SPI interface based on a design concept by [Niklas Ekström](https://github.com/niklasekstrom/amiga-par-to-spi-adapter)

It's quite useful for transferring files to and from the Amiga 500 and other Amiga models that doesn't have a PCMCIA interface or any other interface for mass storage devices.  
The difference from some previous designs is that this version is very small and fully integrated.  
It has a USB-C connector for power because the parallel port doesn't supply any power. It should be possible to take power from another port such as the floppy port or maybe even the joystick ports(?) if you have an adapter for that but I prefer to use an external power source to avoid damaging my Amiga.

A suitable Amiga driver for this device was developed by Niklas Ekström. The source code and a compiled driver can be found in his [release archive](https://github.com/niklasekstrom/amiga-par-to-spi-adapter/releases).

I have designed a 3D-printable enclosure which can be found at https://www.thingiverse.com/thing:6799759/files

## Installation
You need the spisd.device driver in Devs: and most likely the [fat95 DOS handler](https://aminet.net/package/disk/misc/fat95) in L: and you need a suitable mount file, either in Devs:DOSDrivers for auto-mounting or in a convenient location for mounting on demand.  
I have a suitable mount file (SD0) in the [amiga](amiga/) folder in my Github repository.

### Warning:
Do **NOT** insert or remove the device while the computer is running.

## BOM
|Parts|Device|Value|Qty|
|-----|-----|-----|-----|
|C1, C2, C6, C8|Ceramic capacitor 0805|100nF|4|
|C5, C7|Tantalum capacitor 0805|10uF/10V|2|
|C3, C4|Ceramic capacitor 0805|30pF|2|
|R1, R7|Resistor 0805|10kΩ|2|
|R2, R3|Resistor 0805|5kl|2|
|R4|Resistor 0805|100R|1|
|R5|Resistor 0805|100kΩ|1|
|R6|Resistor 0805|560R|1|
|IC1|MCU 32-TQFP|ATmega328|1|
|IC2|3.3V regulator SOT-223|1117-3.3|1|
|IC3|Quad bus buffer|74LVC125A|1|
|Q1|P-channel MOSFET SOT-23|BSS84|1|
|D1|LED|3mm LED|1|
|Y1|16MHz Crystal|ECS-160-20-3X-TR|1|
|J1|D-Sub Male|25-pin|1|
|J2|8-pin push-push MicroSD connector|Würth 693071020811|1|
|J3|USB-C Connector|Molex 2171750001|1|
|J4|ICSP-6 header (optional)|2x3-pin|1|

#### Some notes about the parts in the BOM
The crystal capacitors C3 and C4 should ideally match your crystal but in general it will work just fine with any capacitors around 20-30pF.

The voltage regulator is a 3.3V 1117 type regulator. These are available from plenty of manufacturers and the exact part numbers vary. Use whatever you can find.

The D-sub can have either through hole pins or solder cups. I prefer solder cups as they provide a tighter fit over the PCB edge.

The ICSP header is a regular 2x3 pin-header. I usually leave it out and use a 2x3 pogo pin adapter for uploading firmware. It's also posible to just stick a connector into the slots and push it gently sideways to make contact while uploading the firmware.

The original design was based around an ATmgea328-based Arduino Nano module but with this board a wide range of ATmega328/168/88/48 MCU:s can be used, at least with the current firmware version. Use whatever you can lay your hands on for the day. ATmega48/48A/48PA/88/88A/88PA/168/168A/168P/168PA/328/328P/328PA should all work but I don't think the PB variants will work. At least not without modifications.

A compatible MicroSD connector can be found on AliExpress at a much better price than the Würth connector: https://www.aliexpress.com/item/32802051702.html  
