#USB-Hopper

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


##Usage Scenarios

* directly connect ESP8266 mcus to power and program them
* connect arduino boards and use the leds to show pins switching
* use rs485 to debug housebus installations or transmit data over long distances


##Errata

* RS485 termination is wrong


##Missing Features

* Additional circuity for programming esp8266 supporting RESET
* Use KiCAD instead of Eagle
* Better isolation of Sense pins
* JTAG is not working well with FT232R and so didn't manage to get in.

