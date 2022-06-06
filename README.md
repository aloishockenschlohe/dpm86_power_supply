# dpm86_power_supply
Shellscript for using DPM8600 Series power supply.

Needs socat installed.

Usage:
 
 ./dpm86ng function <action> <parameter>

Details:
 
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

Examples:

        - Turn output off
           user@mybox:~$ ./dpm86 output off
           ok
        - Read output state
           user@mybox:~$ ./dpm86 output
           0
        - Turn output on
           user@mybox:~$ ./dpm86 output on
           ok
        - Read output state
           user@mybox:~$ ./dpm86 output
           1
        - Read actual delivered current (returned value has to be divided by 1000)
           user@mybox:~$ ./dpm86 current
           1255
        - Set the target to 1.3 A
           user@mybox:~$ ./dpm86 current 1300
           ok
        - Read the target for the current (returned value has to be divided by 1000)
           user@mybox:~$ ./dpm86 current target
           1300
        - Read the temperature
           user@mybox:~$ ./dpm86 t
           39
 
Should work with:

- DPM8605 (see f. e. https://joy-it.net/en/products/JT-DPM8605)
- DPM8608 (search on ebay)
- DPM8616 (search on ebay)
- DPM8624 (see f. e. https://joy-it.net/en/products/JT-DPM8624)

! Be aware !
 
1) The power supply has to be set to "simple protocol".
2) You have to install the tool socat.
3) You have to place the file 'basic_functions' in the same directory.
4) Check the variable 'tty' in order to choose the right ttyUSB-device.
5) This script comes along with no warranty for whatever. You have been warned.
6) Have fun.
 
