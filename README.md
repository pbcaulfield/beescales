# Bee Scales
The aim of this project is to calculate the weight of a beehive over a variable time step over the course of a day. This can then be sent in a batch or at each measure to a wifi receiver and therefore to a server directly. ... or something like this.

This project will contain information on software, hardware and implementation, as well as research into existing solutions and limitations with current technology identified.

The aims are for:
- Open source
 - Users should be able to modify and change what they want to, how they want to and be able to understand the project
- Low maintenance
 - Set and forget mentality
- Low cost
 - Current options are at least $2-500
- Flexible
 - Allowing for all use cases, and allowing for upgrades and improvements as required
- Usable
 - Trying to design for all users where possible trying to keep in mind; access, cost, reliability, and ease of installation/use
 
 This is obviously a high aim, but I believe somehow possible. I want a solution which can be for hobbyist beekeepers AND for professionals.

To do:
- [ ] Research existing solutions
- [ ] Hardware choice and design
- [ ] Scale software design
- [ ] Server side software design
- [ ] Prototyping and testing

## Research
Current bee scale solutions are costly, difficult to design. More to be done here. Watch for more.

## System Concept
The system includes the following at this point:
- Bee Scale Hardware
- Server to recieve the data from bee scales

Possible upgrades
- Intermediate step, wifi reciever with mobile/sattelite/other rf connection to base station for remote solutions

## Hardware
At this point the hardware list includes the following chips:
- Arduino Nano (using the ATMEGA328)
 - This is an extremely low power board and cheap, and can be used via batteries, with idle consumption of around 4.5nA. At this consumption the limiting factor becomes the battery chemistry, and not the electronics.
 - http://www.home-automation-community.com/arduino-low-power-how-to-run-atmega328p-for-a-year-on-coin-cell-battery/
 - http://gammon.com.au/power (thank you Nick Gammon, I will mucho appreciato your information if I ever get to doing this project)
 - Approx $3.05 ea
- Temperature sensor/Humidity/Atmospheric measuring
 - Needs more research
- HX711 connected to two load cells (up to 25kg each per corner, allows for measuring up to 100kg)
 - Adding another two load cells will probably not change the accuracy enough to worry about, something to consider in testing
 - The HX711 will probably need temperature calibration, and therefore temperature and atmospheric measurements are becoming more and more likely
 - $1.15 EA
- Mosfet to actuate the ESP8266 and the HX711
 - Reduced power consumption this way, probably, will test
 - Less than $1 each
- ESP8266
 - Wifi module, requires programming, and testing, as however likely this will be easy enough to implement and cheap
 - http://blog.huntgang.com/2015/01/20/arduino-esp8266-tutorial-web-server-monitor-example/
 - https://blogs.msdn.microsoft.com/abhinaba/2016/01/23/esp8266-wifi-with-arduino-uno-and-nano/
 - http://www.ebay.com.au/itm/Hot-Wireless-Module-WIFI-to-UART-Module-ESP8266-ESP-01-AP-STA-WIFI-Remote-/302130701910?var=&hash=item465864a656:m:m38nUDljxKv-NFNMn6VJZOg
  - $2.33
- Load Sensor
 - 25kg each, using two half bridge per scale, similar to these off ebay
 - http://www.ebay.com.au/itm/4pcs-YZC-161D-Body-Load-Cell-Scale-Electronic-Weighing-Sensor-75Kg-Half-Bridge-/281657387887?hash=item419416ab6f
 - $1.50 ea, $3.00 per scale
- DC-DC convertor for the ESP8266
 - http://www.ebay.com.au/itm/2x-DC-5V-to-3-3V-Step-Down-Power-Supply-Module-AMS1117-3-3-LDO-800MA-SOZ-/161745297781?hash=item25a8c56175
 - AMS1117: $0.72 ea
- Batteries
 - Probably go with replaceable, AA or 9V, or coin cells for ease of replacement, will look into power characteristics, life expectancy, and usability.
- Enclosure
 - Looking into some kind of water resistant enclosure, maybe rectangular PVC/HDPE with end caps
 - https://www.bunnings.com.au/icon-plastics-100-x-65mm-x-3m-rectangle-pvc-downpipe_p4773277
 - Though for prototype, will be wooden enclosure, solid piece with centre routed. Further to follow
 
 Estimated cost thus far:
|   Part   |   Cost   |
|----------|----------|
|Nano      |     $3.05|
|HX711     |     $1.15|
|Mosfets   |     $2.00|
|ESP8266   |     $2.33|
|L.Sensor  |     $3.00|
|DC-DC C.  |     $0.72|
|----------|----------|
|Total     |    $12.25|
|----------|----------|
As such excludes batteries, charging, connectors, atmospheric monitoring, etc etc as well as server side componentary.
Adding in a rough estimate, BOM should be around or less than $25 AUD.


## Scale side software(firmware?)
Scale software should be designed to aim to maximise battery life and be updateable OTA.
- Scale checks weight every 5 minutes
- Low power mode for the remainder of the time
- Once per (day?) upload data to server at specific time somehow via wifi module, including;
  - Measured weights
  - Battery life
  - Temperature/Atmospheric monitoring
- And recieve download of updates to variables such as:
  - Polling speed
  - Time of upload
   - The time of upload should be staggered to allow for multiple devices to connect to the same server side firmware, and therefore allow for this to become eventually low powered also

## Server Software
Server software should be HTTP based, allow for access from mobile phones
Allow for programming devices via server interface. Try and use some kind of bootstrap to make it pretty. We shall see though.
Allow for seeing data in a useable way, otherwise the whole concept of measuring is poop.
Allow for adding data about hives, such as adding boxes, frames, harvesting honey, replacing frames, queening, requeening. In batches or for single hives. Grouping hives.
Eventually allow or even suggest uploading data from your hives to a open source data information. If you keep it to yourself, thats not very nice.



If you get here, I hope you don't to be honest. I will only be working on this sporadically. however, hopefully eventually this will become something. And I'll have no excuses to check the bees.
P.
