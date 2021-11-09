# ESPHome-4-4-Light-Driver
**Small light driver with 4 AC SSR outputs and 4 optoisolated inputs for switches, designed for Home Assistant.**

![EH-4A Midi](resources/EH-4AMidi.jpg)
![Upper board](resources/Top_PCB.jpg)
![Main board](resources/Bottom_PCB.jpg)


## Design
Not so much to describe - just ESP with power supply and I2C expander, where four ports are used as inputs and four as outputs. Design of inputs and outputs is used by me from a years with other Home Automation systems (old stuff based on AVR CPUs, currently swapping by a bit more modern, HomeAssistant compatible devices), without any problems.  
Outputs are made as SSR relays, switched with zero-cross detection. It means safe switching of any active  load like lamps, etc, but reactive load is not allowed here, so please don't use this device with any induction load, like e.g. engines.   
Inputs are designed for use momentary buttons, each input port responds to shorting it with the COM output. Needed wiring of inputs (and outputs) is shown on schematic diagram, with grey lines.  

**WARNING! Don't connect input lines with AC installation or any external power lines, it must be fully separated, only direct connections to switch buttons are allowed**   


## Parts and components
Base of this device is an ESP-07 module, choosen due to possibility to connect external antenna. If it is not needed, can be used also ESP12 or any other with the same footprint.
All other components are listed in BoM file.   

Connection between boards can be done by any method, pins have to be connected 1:1.   
Due to reverse connection will damage ESP module, I would recommend to use any method, which avoid of it. Connector like  Molex KK mwould be the best solution, any other with raster 2,54 will be also ok. (on my prototype I used ordinary goldpin connector with one pin more than needed, this pin is removed and corresponding pin in the plug is blinded by glue).

![Connector](resources/down-up_connector.jpg)

Terminals - any 5,08 can be used.  
PSU: popular chinese HLK-PM01, 5V/0.6A  

## Assembly

Both PCBs are prepared for standard DIN rail box case Gainta D3MG http://www.gainta.com/en/d3mg.html, nothing more is needed for assembly, both PCBs fit on latches inside the case.    
External antena is optional, you can use it or stay with internal - up to you. When device is mounted inside of metal switchbox, external antenna mounted outside of box is strongly recommended.  
Stickers should be printed on self-adhesive paper.  


## Software

From ESP-Home perspective it is really simple device, shouldn't be any problems with code. Basic proposal is added into the files, each input controls its corresponding output, whre "short" click on the button just switch on or off the light, "long" click (press and hold more than 1s) switches off all outputs (really useful option for fast switching off the lights in the room). Clicks shorter than 50ms are ignored (debouncing), longer than 3s are also ignored (could be additionally reported as a short circuit on the line). Additionally line 4 contains a timer:   
