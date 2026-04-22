# LED Display Documentation
Taken from Stationeers Community Wiki (Stationeers-Wiki.com) for personal reference only. 

## Mode Values
These lists the values and meanings for the "Mode" property of the LED Display.

Value 	Meaning 	"Setting" parameter interpretation
0 	Normal number display 	Direct display as a number. Values smaller than 1.000E-07 will be displayed as 0.
1 	Percentage number display 	Input range of 0.0 to 1.0 is interpolated and displayed as the range 0% to 100%. Values outside this range scale more, e.g. 10 shows as 1000%
2 	Power display 	Adds a watt suffix (W) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. kW)
3 	Kelvin display 	Adds a Kelvin suffix (K) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. kK)
4 	Celcius display 	Adds a degrees Celcius suffix (°C) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. k°C)
5 	Meters display 	Adds a meters suffix (m) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. km)
6 	Credits display 	Adds a Credits suffix (€) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. k€)
7 	Seconds display 	Adds a seconds suffix (sec) to the number. Does not divide and apply a metric prefix for Setting values >= 1000.
8 	Minutes display 	Adds a minutes suffix (min) to the number. Does not divide and apply a metric prefix for Setting values >= 1000.
9 	Days display 	Adds a days suffix (days) to the number. Does not divide and apply a metric prefix for Setting values >= 1000. Always indicates "days" even when Setting is 1.
10 	String display 	Displays the Setting value as an octet-packed ASCII string of up to six characters. A Setting value of $414243444546 will display "ABCDEF" on the display.

A Logic Memory Unit value of 71752852194630 will display "ABCDEF" on the display.
11 	Farenheit display 	Adds a farenheit suffix (°F) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. k°F)
12 	Litres display 	Adds a Litres suffix (L) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. kL)
13 	Mol display 	Adds a Mols suffix (mol) to the number. Also divides the number as needed and adds a metric prefix to the suffix. (e.g. kmol)
14 	Pa display 	Adds a Pascals suffix (Pa) to the number. Also divides the number as needed and adds a metricprefix to the suffix. (e.g. kPa)

## Data Parameters
These are all parameters that can be written with a Logic Writer, Batch Writer, or Integrated Circuit (IC10).

Parameter Name 	Data Type 	Description
Mode 	Integer 	Sets the display mode of the LED Display to the passed value. (See Mode Values)
Setting 	Float 	Sets the raw number to display on the LED Display.
On 	Boolean 	Turns the LED Display on, when set to 1. Turns it off, when set to 0.
Color 	Integer 	Sets the color of the text on the LED Display. (See Data Network Colors)

## Data Outputs
These are all parameters, that can be read with a Logic Reader or a Slot Reader. The outputs are listed in the order a Logic Reader's "VAR" setting cycles through them.

Output Name 	Data Type 	Description
Power 	Boolean 	Returns whether the LED Display is turned on and receives power. (0 for no, 1 for yes)
Mode 	Integer 	Returns the mode of the LED Display. (See Mode Values)
Error 	Boolean 	Returns whether the LED Display is flashing an error. (0 for no, 1 for yes)
Setting 	Float 	Returns the "Setting" value of the LED Display.
On 	Boolean 	Returns whether the LED Display is turned on. (0 for no, 1 for yes)
RequiredPower 	Integer 	Returns the current amount of power, required by the LED Display, in watts.
Color 	Integer 	Returns the color setting of the LED Display. (See Data Network Colors) 
