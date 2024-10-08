# ESP32-Alarm-Notifier
An ESP32-based system for monitoring 24V analog alarm signals triggered by sensors throughout a farm. The software side of the system is made with ESPHome, Node-RED and Home Assistant. The ESP32 used is the Olimex ESP32-POE-ISO-IND, but any PoE powered ESP32 would have worked.

<Picture of the final setup>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/b2975e0b2926ca92acbed9962f9581ac3c3f229b/resources/final_setup.jpg?sanitize=true" width="1000">


## Problem description
There are 5 LEDs that represent alarms in different buildings. In order to find out whether a problem has occurred, and where said problem is, one must check these LEDs. The goal is to get these LEDs into Home Assistant as binary sensors, and notify me when a problem has occurred in any of the buildings. 

The five alarms can be simplified as seperate 24V circuits each containing an LED and an on/off switch.

<Picture of a simplified circuit>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/018acbf1bb7f07c3b3919d12287a3a8b39f2a799/resources/simple_curcuit.png?sanitize=true" width="600">


## Hardware & Solution
As I wanted to learn the basics of designing PCBs, I figured i could try to design a simple PCB that could solve this problem. Additionally, the ESP32 had to be powered using PoE (to minimize cabling). After searching for boards around the internet, I settled for the Olimex ESP32-POE board. The idea was simple. I wanted to intercept the signal on each LED using optocouplers. The collectors were connected to their own GPIO pin, with ESP32's internal pullup resistors, and the emitters were connected to ground. The simplified circuit with an optocoupler can be seen in the picture below.

<Picture of simplified circuit with opto>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/018acbf1bb7f07c3b3919d12287a3a8b39f2a799/resources/simple_circuit_with_opto.png?sanitize=true" width="600">


The KiCAD files for the final design of the PCB can be found in the repository. 

<Picture of the PCB schematics>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/018acbf1bb7f07c3b3919d12287a3a8b39f2a799/resources/schematics.png?sanitize=true" width="800">

<Picture of the PCB circuit>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/018acbf1bb7f07c3b3919d12287a3a8b39f2a799/resources/PCB.png?sanitize=true" width="800">

<Render of the PCB in KiCAD>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/018acbf1bb7f07c3b3919d12287a3a8b39f2a799/resources/Render_PCB.png?sanitize=true" width="800">

<Picture of the PCB with components>
<img src="https://github.com/TheMipmap/ESP32-Alarm-Notifier/blob/90b5f87b90269a34607039360a7028930a952716/resources/PCB_with_components.jpg?sanitize=true" width="800">


