Ender-2-Pro-V427

This code is based off of Marlin's source code.

back history on why this repo was created.

The Ender-2 Pro originally shipped with a version 4.2.3 mainboard that was similar to a version 4.2.2 mainboard with the differences being that it had one changed pin location and it had 5 pin motor connectors instead of the usual 4 pin motor connectors that previous Creality boards have.

It took a while for the source code to become available for 4.2.3 mainboards but it is now available.

Most recently, another new variant of the mainboard has shown up in the wild on newer Ender-2 Pro printers, version 4.2.S4. Unlike previous versions this board is not a STM32 or GD series chip. It in fact uses a HDSC HC32F460 chip and there is no source code available for it. I ran into bad stuttering issues with this mainboard when trying to run prints on my Ender-2 Pro using Octoprint. Thinking that I had a faulty or poor quality USB cable, I swapped it out for a high quality cord with RF chokes on each side of the cable and gold plated contacts and connectors on both sides of the cable, but it didn't fix the issue. I also tried swapping out for a different system for Octoprint thinking that this might help, but it didn't.

I contacted Creality Technical support multiple times asking for a copy of the source code for this specific mainboard, only to get vague responses pointing me to their public GitHub Repositories which DO NOT have a repo for this specific board. When I called them out on this, the only response I got was that it's not available.

I looked around and found a few posts online talking about this specific chip being used on an Artillery Kobra, and after going thru the process of getting that source code and setting up the required programs to try to compile it, everything is so different between any marlin source code, config files,etc. in the source for that firmware I couldn't figure out how to use it with the available 4.2.3 source code and config files to make a working firmware bin file to flash on the 4.2.S4 mainboard.

This repo uses modified Ender-3 Pro Version 4.2.7 source code and config files with changes merged in from the Creality Ender-2 Pro configuration files to make a working firmware for a Ender-2 Pro for a version 4.2.7 mainboard.

The major changes for the config files are as follows.

used the status screen and boot screen config files from the Ender-2-Pro V4.2.3 config to make sure the screen shows the correct info in the upper left corner for the status screen 
edited the custom name so the info at the bottom of the screen shows Ender-2 Pro 4.2.7 ready
edited the max sizes for X,y, and Z to be the correct sizes for a Ender-2 Pro edit the x, and y min positions to match the ones set in the config for the Ender-2 Pro 4.2.3 mainboard
enabled S_CURVE_ACCELERATION enabled LCD_BED_TRAMMING to help assist with tramming the bed corners. increased the baud rate for the serial connection to 250000, I am not sure if this will help so I may revert this change after testing it to see if it makes a difference.
enabled INDIVIDUAL_AXIS_HOMING_MENU to turn on individual axis hominh which can be useful over having everything be homed at the same time (example home the X axis so you can then work on the bed surface if youhad to cancel a print and it didn't move the print head out of your way.
I am currently waiting on adapter cables from TH3D to allow me to plug the stock 5 pin connector cables for the motors into the replacement 4.2.7 but the firmware I compiled works, and drives the Ender-2 Pro screen with no issues, and it is seeing the thermistors for the hot end and the heated bed.

After waiting on 5 pin to four pin motor adapter cables that I ordered from TH3D to adapt the cables to work on the 4.2.7 mainboard came (https://www.th3dstudio.com/product/ender-2-pro-stepper-motor-adapter-cable-4-pack/) in I was finally able to fully test out my firmware and after making some adjustments to the initial config files I provided It is now working fully.

Thw code also now has host controls turned on, and I have turned on the head park feature and the M600 filament change command.

Octoprint is running well on this firmware, no more stuttering issues.

I do not plan on keeping this code updated and current from the marlin repository, so If you wish to do so, use the config files I have in the marlin folder to build your own branch of the code.

Thank You,

DoctorEvil30564
