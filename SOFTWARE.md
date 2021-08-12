The firmware for the Tree of Life badge is delivered as a .UF2 file. 

It was developed in Micropython and frozen to a .UF2, similar to how a C application is compiled into a .UF2.

In case you're unfamiliar with flashing the Pico, here are the basic steps.

1. To access the bootsel button (white plastic button on the Pico surface, you can either unscrew just 
the bottom screw on the badge, pull it apart about an inch, and slide your finger between the boards, or
use a credit card. Fiddle around until you can feel/hear the click, and then

2. Connect USB to computer, and then the microUSB end to the Pico while holding down bootsel.

3. The Pico boot partition should mount in your computer as RPI something.

4. Drop a new UF2 onto that volume. It will transfer, then restart running that UF2.  Depending on what you're doing, 
it might be recommended to drop the flash_nuke.uf2 on it first. That clears out the pico better than just replacing 
the firmware. If you drop flash_nuke, the RPI volume will mount again after transferm, at which point you can drop your 
firmware. You shouldn't need to hold bootsel again after dropping flash_nuke.

5. Alternately, if you launch Thonny after the bootsel or bootsel/flashnuke combo, when you hit STOP in Thonny, and Thonny
is able to see your badge as a Pico on the USB port, it should offer to install the MicroPython firmware for you.

6. To get the ToL stock firmware back on it, bootsel, then flashnuke, then drop the tol_0.1.0.uf2 onto the RPI volume.
