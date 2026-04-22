# Filtration Automation

For use with an IC10 chip in a "Filtration" unit

# Documentation
## List of functions

### start
jump target for resetting if we're outside the main loop. Sets system to idle mode as a safety feature. 

### readslots
Reads key info from the slots on the Filtration device. These two slots can have any gas filters installed in them, but we only evaluate a few key types to work automation on due to program size constraints. We will however check that both filters are present and have some minimum amount of durability remaining. While it's perfectly acceptable to use two different filters in general, it's out of scope for this program to manage that state. 

### safetycheck
Assumes that we're already read the slots on the filter. Checks the following:

* Power off if not slot 0 occupied
* Power off if not slot 1 occupied
* Power off if not s0 filter life > 5%
* Power off if not s1 filter life > 5%
* Power off if not two matching filters

## identifyGasType:
Essentially a case statement that reads our pre-defined constants for the hashes of different filters and then sets the type of gas we're assuming the stationeer wishes to filter for. No particular reason for the numbering scheme, I went with the order the gases are shown on the wiki, from left to right. 

* 1 - Nitrogen
* 2 - Oxygen
* 3 - Carbon Dioxide

## flowcheck
Reads the pressure at the three pipe connections. Sets the machine to idle if we're at risk of wasting power or bursting a pipe. 

## operate
The only function that actually enables the Filtration device for operation. Also changes the stat var and updates the LED colour.

## main
Main program loop. Reads the pressure at input, and writes this out for display to the Stationeer. Counts up until x loops, then runs some checks and resets the count. We don't need to run the checks constantly, every X cycles should be enough. If any important checks fail, we use the state variable to indicate we should shut down and await help, like so: brne rState 1 shutdown

### Checks to run
*  jal readslots
*  jal identifyGasType
*  jal safetycheck
*  jal flowcheck

## shutdown
Turns off the power switch on the Filtration device. Also changes the stat var and updates the LED colour, and the device's mode to idle. 

## idle:
Changes the LED colour, and the device's mode to idle. 


## init:
A tidy way to configure our aliases (Devices/Pins), registers, constants and initialise any variables on boot up. 