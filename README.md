# dpm86

Shellscript for using DPM8600 Series power supply.

## Usage
 
 ./dpm86ng parameter

## Command line arguments
 
           output/o                   -- read the actual output state (on/off)
           output/o 1/on              -- turn the output on
           output/o 0/off             -- turn the output off

           voltage/v                  -- read the actual delivered voltage
           voltage/v <value>          -- set the voltage target
           voltage/v target           -- read the voltage target

           current/c                  -- read the actual deliviered current
           current/c <value>          -- set the target
           current/c target           -- current: read the target

           const/C                    -- read the actual const setting (const voltage/const current)
           const/C voltage/v          -- set constant voltage delivery
           const/C current/c          -- set constant current delivery

           temp/t                     -- read the temperature

           read/r <function>          -- read value from function
           write/w <function> <value> -- write <value> to <function>

## Examples


- Turn output off, read output state, turn output on, read output state again:

           user@mybox:~$ ./dpm86 output off
           ok
           user@mybox:~$ ./dpm86 output
           0
           user@mybox:~$ ./dpm86 output on
           ok
           user@mybox:~$ ./dpm86 output
           1
           user@mybox:~$ 
           
- Read actual delivered current (returned current has to be divided by 1000).

           user@mybox:~$ ./dpm86 current
           1255
           user@mybox:~$ 

- Set the current target to 1.301 A (desired current has to be multiplied by 1000) and read it.

           user@mybox:~$ ./dpm86 current 1301
           ok
           user@mybox:~$ ./dpm86 current target
           1301
           user@mybox:~$ 

- Read actual delivered voltage (returned voltage has to be divided by 100).

           user@mybox:~$ ./dpm86 v
           2120
           user@mybox:~$ 

- Set the voltage target to 25.3 V (desired voltage has to be multiplied by 100) and read it.

           user@mybox:~$ ./dpm86 voltage 2530
           ok
           user@mybox:~$ ./dpm86 v target
           2530
           user@mybox:~$ 

- Read the temperature

           user@mybox:~$ ./dpm86 t
           39
           user@mybox:~$ 
 
## Should work with

- DPM8605 (see f. e. https://joy-it.net/en/products/JT-DPM8605)
- DPM8608 (search on ebay)
- DPM8616 (search on ebay)
- DPM8624 (see f. e. https://joy-it.net/en/products/JT-DPM8624)

## Be aware!
 
1. The power supply has to be set to "simple protocol". Please check the manual.
2. You have to place the file 'basic_functions' in the same directory.
3. Check the variable 'tty' to choose the right ttyUSB-device.
4. This script comes along with no warranty at all. You have been warned.
5. Have fun.
