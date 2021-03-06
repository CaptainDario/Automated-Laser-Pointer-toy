"DaPetToy" is an automated pet-Laser-Pointer toy.
It randomly moves a laser pointer on two axes so that a pet could chase it.

I made this for the 2020 ["Pets Speed Challenge"]((https://www.instructables.com/id/An-Automated-Cat-laser-pointer-toy/) ) on instructables (The instructable has more images for the setup of the hardware).
See it in action by clicking on the image below. </br>
[![See it in action](https://img.youtube.com/vi/vp5igMt3IM0/0.jpg)](https://www.youtube.com/watch?v=vp5igMt3IM0)


## Instructions

## Flashing the software
You can compile the software from source and flash the data and firmware this way.
But here I will describe how to flash the software via the ready-made images provided [here.](https://github.com/CaptainDario/Automated-Cat-Laser-Pointer-toy/releases) </br>
First you will need a [python install](https://www.python.org) with the [esptool](https://github.com/espressif/esptool) module installed.
```
path\to\your\python.exe -m pip install esptool
```
Now you are ready to write the firmware and data image:
```
path\to\your\python.exe -m esptool -b 921600 write_flash 0x0 firmware.bin 0x00300000 spiffs.bin
```

**Caution:** </br>
Depending on the esp board you are using the offset where to write the 'spiffs.bin' can be different!

Now you can power up your esp.
After some time it should open a access point called 'DaPetToy'.
The webserver IP address is the standard esp webserver address: </br>
```192.168.4.1``` </br>
Enter it in your browser and you will be greeted with a screen to enter you WiFi credentials.
The ESP will reboot after submission of the credentials.
If everything is correct you can now look up the ip address of your ESP and connect to it from your home network.

But for now you have to do the following:You need to rename the file “REMOVE_credentials.h” in the “src” folder to “credentials.h”. And replace “YOUR SSID” and “YOUR PWD” in this file with your wifi SSID and password.
After completing this first step you have to upload the file system to the esp and than compile and upload the software.

## Hardware
You need following hardware for this project:

* [3.3V laser pointer](https://www.aliexpress.com/item/32676284654.html?spm=a2g0s.9042311.0.0.27424c4dB5clXD)
* [ESP D1 mini](https://www.aliexpress.com/item/33036965281.html?spm=a2g0o.productlist.0.0.4ccc4b07HOS6x9&algo_pvid=bc3ef8fe-2a08-46af-b766-844a65c69a65&algo_expid=bc3ef8fe-2a08-46af-b766-844a65c69a65-8&btsid=0b0a0ad815928792906667495eca52&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)
* Some jumper wires
* [barrel jack for power](https://www.aliexpress.com/item/32883658107.html?spm=a2g0s.9042311.0.0.27424c4dngOKlg)
* 2x [ULN2003 stepper motors with driver board](https://www.aliexpress.com/item/32962476866.html?spm=a2g0o.productlist.0.0.6ad63f4eT367Qu&algo_pvid=4c8276b2-4e30-4886-951e-bd294634acb4&algo_expid=4c8276b2-4e30-4886-951e-bd294634acb4-12&btsid=0b0a187b15928792542952779e343a&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)
* [5V 2A PSU](https://www.aliexpress.com/item/4000102102421.html?spm=a2g0o.productlist.0.0.c70945e3c7KZNP&s=p&ad_pvid=202006222023487857474908802500001954491_4&algo_pvid=c8b813d4-ded6-4fb1-b736-55e24e119589&algo_expid=c8b813d4-ded6-4fb1-b736-55e24e119589-3&btsid=0b0a050115928826284412892e2f08&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_)
* 1x M4×10 screw and nut
* 2x M4×20 screw, nut and washer
* 3D printer
(All those components are just examples)

First you need to print the mounts for the motors. 
When you downloaded the newest release it will contain a folder called 'models' which will contain the necessary .stl files.

A little bit harder will be the making of the base case. I made the case out of wood to provide more structural rigidity (and I think it looks nicer too). The base case has one large hole on the top and a small one on the side. The large hole is for the stepper motor and the small one for the power input. Make sure that the motor-hole is large enough to fit the cables of two stepper motors and also the two wires of the laser pointer (they need space to move freely as the wires will move due to the rotation).

Now connect the components as shown in this image:

![circuit.png](./instructions/wiring/circuit.png)

Now it is time to assemble it. First put the laser pointer in the mount and use the M4x10 screw and nut to fix it in place.
Next up is the power jack. Put it in the small hole and fasten it with its nut.
The first motor has to be put in the 3D printed mount and secured with the two M4×20 screws, nuts and washers.
In the second last step the other motor has to be placed in the large hole of the wood case while routing all the cables through the hole too.
Finally put the motors in their holes and also stick them together. If they do not fit tightly put some hot glue on them to secure everything in place.


#### Caution
* Double check that the cables have enough space to move while the motors are rotating. 
* NEVER rotate the motors by hand! You can and most probably will damage them.
* Motors tend to overheat during extend usage. Since this is a cat toy, stop it if it is not in use to prevent it from overheating.




## Project Ideas and next steps
You can take a look at the planned tasks [here](https://github.com/CaptainDario/Automated-Cat-Laser-Pointer-toy/projects/1).
If you have ideas for new features or improvements feel free to open a request.


## Developer notes
This project uses [Circuit Daiagram](https://www.circuit-diagram.org/) for wiring images.
