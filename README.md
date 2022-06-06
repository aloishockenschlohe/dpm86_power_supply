# dpm86_power_supply
Shellscript for using DPM8600 Series power supply.
Needs socat installed.

 Usage:
 
 ./dpm86ng facility action parameter

 Details
 
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


Should work with:

- DPM8605 (see f. e. https://joy-it.net/en/products/JT-DPM8605)
- DPM8608 (search on ebay)
- DPM8616 (search on ebay)
- DPM8624 (see f. e. https://joy-it.net/en/products/JT-DPM8624)

! Be aware !
The power supply has to be set to "simple protocol".
