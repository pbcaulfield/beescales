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
Current bee scale solutions are costly, difficult to design, 

## System Concept
The system includes the following at this point:
- Bee Scale Hardware
- Server to recieve the data from bee scales

Possible upgrades
- Intermediate step, wifi reciever with mobile/sattelite/other rf connection to base station for remote solutions

## Hardware
At this point the hardware list includes the following chips:
- Arduino Nano (using the ATMEGA328)
 - This is an extremely low power board, and can be used via batteries, with idle consumption of around 4.5nA. At this consumption the limiting factor becomes the battery chemistry, and not the electronics.
 - http://www.home-automation-community.com/arduino-low-power-how-to-run-atmega328p-for-a-year-on-coin-cell-battery/
- Temperature sensor/Humidity/Atmospheric measuring

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
