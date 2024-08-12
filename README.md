# ESP32-Alarm-Notifier
An ESP32-based system for monitoring 24V analog alarm signals triggered by sensors throughout a farm. The system is made with ESPHome and Home Assistant.

<Picture of the final setup>

## Problem description
There are 5 LEDs that represent alarms in different buildings. In order to find out whether a problem has occurred, and where said problem is, one must check these LEDs. The goal is to get these LEDs into Home Assistant as binary sensors, and notify me when a problem has occurred in any of the buildings. 

The five alarms can be simplified as seperate 24V circuits each containing an LED and an on/off switch.

<Picture of a simplified circuit>

## Hardware & Solution
As I wanted to learn the basics of designing PCBs, I figured i could try to design a simple PCB that could solve this problem. Additionally, the ESP32 had to be powered using PoE (to minimize cabling). After searching for boards around the internet, I settled for the Olimex ESP32-POE board. The idea was simple. I wanted to intercept the signal on each LED using optocouplers. The collectors were connected to their own GPIO pin, with ESP32's internal pullup resistors, and the emitters were connected to ground. The simplified circuit with an optocoupler can be seen in the picture below.

<Picture of simplified circuit with opto>

The KiCAD files for the final design of the PCB can be found in the repository. 

<Picture of the PCB schematics>
<Picture of the PCB circuit>
<Render of the PCB in KiCAD>
