Hardware documentation:

The platform is the Raspberry Pi Pico, using the RP2040 processor.

The pinouts hard-wired into the PCB are as follows:

1. 32 WS2812B-2020 LEDs:

Pico Pin 11 is wired to the DI (Data In) pin of SP10. Each DO (Data Out) pin is wired to the DI (Data In) pin of the next LED.
The wiring sequence of LEDs can be understood as follows: 

The Spheres (Sephiroth) are numbered 1 through 10. Sphere 10 is LED 0.
The Paths are numbered 11 through 32. 
Here are example Python list objects describing them by referencing their LED address:

self.spheres = [31, 27, 25, 20, 18, 15, 7, 9, 4, 0]
self.paths = [28, 30, 29, 26, 22, 21, 23, 24, 19, 14, 13, 16, 17, 12, 11, 10, 8, 6, 3, 5, 2, 1]

Where the actual number for the sphere on the board is +1
and the actual number for the path on the board is +11.

If someone wants to articulate that better, that's great.

--------

2. SSD1306 OLED

Some boards are GND/VCC/SCL/SDA, and others are VCC/GND/SCL/SDA on the OLED port. Pay attention to which if you replace them, 
or be prepared to figure out how to cut traces and swap them.

SDA is wired to Pin 12 on the Pico.
SCL is wired to Pin 13 on the Pico.

--------

3. Tactile switches (buttons)

We're using 4mm x 4mm tactile switches. They are wired as follows:

SW1: 0
SW2: 1
SW3: 2
SW4: 3
SW5: 10
SW6: 8

--------

4. SAO v1.69bis connector(s)

We implemented the advanced (6-pin) Shitty Add-On spec. I heard a rumor at DC29 that there's a new spec being discussed.

But for now, we have power, ground, the same I2C chain as the OLED, and GPIO15 and GPIO5 are wired to the GPIO pins of the SAO.

--------

5. NRF24L01+

This is the wireless transceiver used for badge-to-badge communications.

3V3
GND
GPIO10->MOSI
GPIO4->MISO
GPIO6->SCK
GPIO15->CSN
GPIO14->CE
We did not wire the IRQ connector as we didn't need it with our application.

========

Anyhow, I hope this documentation helps for those who want to hack the Tree of Life badge to run your own applications.

We're putting the UF2 of the stock firmware in this repo in case you need to reflash it.

Otherwise, generate your own UF2 from C, or flash with MicroPython and code it directly. There's lots of stuff out there, and it's
pretty well-documented.

Thanks again for supporting the Tree of Life badge. We are humbled by the response from the community. Turns out either there are
far more esoteric nerds in the community than we thought, or we just made it beautiful enough to lure people to the dark side...
or maybe both.

We'll be back next year with something cool. We're already thinking about it. Because we're masochists and this is a really good 
relief valve for excess nerd energy when our jobs don't challenge us enough. :)

Thanks for everything!

-baab (@dc540baab)
-lyra (@burningblack430)
-kevin (@mytechnotalent)

and the rest of the DC540 team!
