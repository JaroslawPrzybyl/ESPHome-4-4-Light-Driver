# ESPHome-4-4-Light-Driver
**Small light driver with 4 AC SSR outputs and 4 optoisolated inputs for switches.**



Base of this device is an ESP-07 module, choosen due to possibility to connect external antenna. If it is not needed, can be used also ESP12 or any other with the same footprint.
All other components are listed in BoM. 

Connection between boards can be done by any method, pins have to be connected 1:1. 
Due to reverse connection will damage ESP module, I would recommend to use any method, which avoid of it. Connector like  Molex KK mwould be the best solution, any other with raster 2,54 will be also ok. (on my prototype I used ordinary goldpin connector with one pin more than needed, this pin is removed and corresponding pin in the plug is blinded by glue).
Terminals - any 5,08 can be used.
PSU: popular chinese HLK-PM01, 5V/0.6A
Both PCBs are prepared for standard DIN rail box case Gainta D3MG http://www.gainta.com/en/d3mg.html, nothing more is needed for assembly.
External antena is optional.
