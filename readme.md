#USB-Hopper

![USB Hopper PCB design](layout.png?raw=true)

*The swiss army knife for working with microcontrollers*

##Features

* Serial interface using a FT232R
* 3 Voltages Powersupply using efficient DC-DC Buck converters:
** 5V directly from USB Bus (500mA)
** 3.3V 600mA
** 1.8V 600mA
** USB suspend supported
** not usable for heating coffee, sorry!
* USB-A Connector (no stupid cables)
* IO voltages selectable via jumper
* Sense / PWR / RX / TX LEDs
* All 4 Leds are multipurpose usable as poor mans osciloscope
* RS485 on board
* multiple comfortable headers
* cool pcb layout with sublimal messages (yea, you can call 2pt fonts sublimal ;)
* different assembly options using less voltages or other voltages, 


##Usage Scenarios

* directly connect ESP8266 mcus to power and program them
* connect arduino boards and use the leds to show pins switching
* use rs485 to debug housebus installations or transmit data over long distances


##Errata

** RN4604 IC must be mounted 180° rotated! **

* RS485 termination is wrong

* USB-Power supply may need less parts


##Missing Features

* Additional circuity for programming esp8266 supporting RESET
* Use KiCAD instead of Eagle
* Better isolation of Sense pins
* JTAG is not working well with FT232R and so didn't manage to get in.
* Make RE/DI controllable by FTDI pins
* Put RTS/DTR on pads (not only pins because they are usefull for esp programming)
* Make external power switchable via some signal lines / jumpers / both


#Files:

* *.brd, *.sch: eagle board and schema files
* *.BOM: Bill of Materials (text)
* parts.ods: Unfinished spreadsheet with incomplete list of parts and where to buy them and what they may have costed a long long time ago.


#Make compile

* Start with the biggest IC: the FTDI chip. There are multiple ways how you can get it on the pcb. In my optinion this is the easiest one: Put as little solder as possible on each pad. Now apply flux from a pen. Place the IC exactly on the pads and using a knife tip on the soldering iron go across the legs. Check e.g. using your mobile and some magnifing app.

* Now solder the small ics like the DC-DC converters, the mosfet and the transistor arrays. Here it works best first putting solder on *one* pad, placing the ic then soldering that one leg. Now the IC can't move anymore and you can solder the other legs easily.

* Then its time for the resistors and capacitors. Apply the same procedure as with the small ICs. I like using my fingernails to hold them while soldering but you can use tweezers, of cause.

* Now put on the remaining stuff. The usb connector and the pin header come last because they go though the pcb so that it can't lay flat anymore which would have been a major anoyance while mounting the other parts.

* finally connect the solder bridges apropriately.

#Brides/Jumpers

![Jumper layout](jumper.png?raw=true)

A. Main Power Supply jumper:

This one controls the power supply for the ftdi io pins and most of the header pins. It can have 4 settings: 5V, 3.3V FT generated, 3.3V Buck generated and 1.8V. 

B. Power LED Jumper + additional Sense pin

Can be used to disconnect the (blue) power led and use it as additional sense pin.

C. Connect RO / DI Pins of RS485 to Rx/Tx of the FT

D. Sense pin. Controls the (red) sense led.

E. Two more sense pins which can controll the Rx/Tx Leds

F. Select supply voltage to the RS485 Transceiver. Depends on the Transceiver used. Normally 3.3V.

G. Connect DE/RE Pins of the transceiver to Vcc/GND. You normally want to do this.

H. Either connect the Tx/Rx LEDS directly to the FT Led pins (jumper closed) or via transistor to the Tx/Rx Lines (jumper open but transistor arrays on the board.)

K. Not really good termination settings.

# Config

The FT232R has many config options. Use the "FT_Prog" utility to change pin mappings and maximum power rating.
