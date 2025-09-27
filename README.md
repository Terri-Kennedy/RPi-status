# RPi-status
Raspberry Pi version / power / cooling status report script

This is an enhanced version of the vcgencmd_power_report.sh script, forked from Paraphraser's original script at:

https://gist.github.com/Paraphraser/17fb6320d0e896c6446fb886e1207c7e

I encourage you to read that article as it contains a great deal of additional useful info which I'm not repeating here.

# Note:
This works properly on a Raspberry Pi 5 with the official "Raspberry Pi Active Cooler" installed. It has not been tested (yet) on a Pi 5 without a cooler installed, although I expect it will simply report 0 RPM.

On a Raspberry Pi 4B, it generates a harmless warning message as the /sys/devices/platform/cooling_fan/hwmon node does not appear in the device tree. This will be fixed - I've just had a number of requests for the script 'as-is'.

It has not been tested on other Raspberry Pi models, and feedback is welcome - just open a new issue report here and I'll add your information.

# Sample output
The following is a representative sample of the display produced by this script:
```
Raspberry Pi 5 Model B Rev 1.0
Linux version 6.12.47+rpt-rpi-2712 (2025-09-16)
vcgencmd get_throttled (0x0)
vcgencmd measure_volts:
     core volt=0.9026V
  sdram_c volt=0.6000V
  sdram_i volt=0.6000V
  sdram_p volt=1.1000V
Temperature: 49.4'C
  Fan Speed: 3038 RPM
Current CPU clock: 2.4 GHz
Minimum CPU clock: 1.5 GHz
Maximum CPU clock: 2.4 GHz
```
# Installation
Just download the status.sh script and use 'chmod 555 status.sh' to mark it as executable. Optionally, use 'cp -p status.sh /usr/local/bin/status' to make it available by simply typing 'status'.

# Note
My impetus for creating this script was using a single large power supply to run eight Raspberry Pi 5 boards, each with an NVM HAT+ and 256GB.2 SSDs. I wanted to make sure the Pis were not throttling. Since the Pi 5 uses USB-C PD to detect the capacity of the attached power supply, I had to override this auto-detection by adding "PSU_MAX_CURRENT=5000" to the EEPROM config. The official socumentation for that setting can be found at:

https://www.raspberrypi.com/documentation/computers/raspberry-pi.html#PSU_MAX_CURRENT

# Credit
Based on an original script from: 

https://github.com/Paraphraser
