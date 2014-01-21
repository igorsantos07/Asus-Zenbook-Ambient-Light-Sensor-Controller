Asus Zenbook Ambient Light Sensor Controller
============================================

Tested with:
------------
 * UX32VD + Ubuntu 13.04 + Linux 3.8.0
 * UX32VD + Ubuntu 13.10 + Linux 3.11.0

How to install
--------------

 1. Install the ALS Driver:
   1. Download the source code from [here](https://github.com/victorenator/als).
   2. Extract the archive, move into the directory, and compile with `make`.
   3. Insert the module into your current kernel with `sudo insmod als.ko`
 2. Install *acpi_call*:
   1. Download the source code from [here](https://github.com/mkottman/acpi_call).
   2. Extract the archive, move into the directory, and compile with `make`.
   3. Insert the module into your current kernel with `sudo insmod acpi_call.ko`
 3. Finally, build this controller:
   1. `qmake als-controller.pro -r -spec linux-g++-64`, or `qmake als-controller.pro -r -spec linux-g++` if you're on a 32-bit system.
   2. `make`
   
The generated binary file, *als-controller*, is what will monitor the light sensor.

How to use
----------
 1. Launch als-controller with root privileges, for example: `sudo ./als-controller`. This will be the service that monitors the light sensor.
 2. Use the same program with user privileges, als-controller, to control the service. Some examples:
    
        ./als-controller -e     // Enable the sensor
        ./als-controller -d     // Disable the sensor
        ./als-controller -s     // Get sensor status (enabled/disabled)

Better, detailed instructions coming soon
