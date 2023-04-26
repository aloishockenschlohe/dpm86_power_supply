# dpm86

Tool for controlling DPM86xx Series power supply via its RS485 interface.

## Usage
 
 ./dpm86 action parameter

## Command line arguments
 
           output/o                                -- read the actual output state (on/off)
           output/o 1/on                           -- turn the output on
           output/o 0/off                          -- turn the output off

           voltage/volt/v                          -- read the actual delivered voltage
           voltage/volt/v <0.0 .. max>             -- set the voltage target
           voltage/volt/v target/setting           -- read the voltage target
           voltage/volt/v max                      -- read the maximum output voltage

           current/c/ampere/amp/a                  -- read the actual deliviered current
           current/c/ampere/amp/a <0.0 .. max>     -- set the current target
           current/c/ampere/amp/a target/setting   -- read the current target
           current/c/ampere/amp/a max              -- read the maximum output current

           power/p/watt/w                          -- read the actual delivered power
           power/p/watt/w target/setting           -- read the power target

           const/C                                 -- read the actual const setting (voltage/const)
           const/C voltage/v                       -- set constant voltage delivery
           const/C current/c/ampere/amp/a          -- set constant current delivery

           temp/t                                  -- read the temperature

           READ/R <function>                       -- read value from function (DANGEROUS!)
           WRITE/W <function> <value>              -- write <value> to <function> (DANGEROUS!)


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
           
- Read actual delivered current

           user@mybox:~$ ./dpm86 current
           12.55
           user@mybox:~$ 

- Set the current target to 1.301 A

           user@mybox:~$ ./dpm86 ampere 1.301
           ok
           user@mybox:~$ ./dpm86 amp target
           1.301
           user@mybox:~$ 

- Read actual delivered voltage

           user@mybox:~$ ./dpm86 v
           21.20
           user@mybox:~$ 

- Set the voltage target to 25.3 V

           user@mybox:~$ ./dpm86 voltage 25.3
           ok
           user@mybox:~$ ./dpm86 v target
           25.30
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
2. Check the variable 'tty' and choose the right ttyUSB-device.
3. DO NOT USE Raspberry 4! After a while a error message shows up ("serial.serialutil.SerialException: [Errno 12] could not open port /dev/ttyUSB0: [Errno 12] Cannot allocate memory: '/dev/ttyUSB0'") and the serial port isn't reachable anymore. Use RPi 3 or RPi Zero (W) instead.
5. This script comes along with no warranty at all. You have been warned.
6. Have fun.
