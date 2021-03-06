# How to make killer robots with Python and Raspberry Pi - Radomir Dopieralski

Robots in popular culture differ substantially from what is available today.
You may see yourself in a role of a mad scientist constructing an army of
robots to take over the world, but when you go to any website about building
robots, you are presented with those... toys. They can't fly, don't have lasers
and death rays, they ride around on wheels, and their main function is to avoid
obstacles. Imagine that! You unleash your robot on the city to wreck havoc and
destruction, and what it does when it faces a building or a police car? Meekly
turns around and rides on its silly plastic wheels? No! The robots I build will
trample the policemen and walk straight into the building, with no regard to
their own safety. That's how it's done!

And no wheels. Wheels are easy -- you basically only need an H-bridge and two
electric motors with gear boxes. And a small battery. Connect the bridge to two
GPIO pins, and you have full control. Pathetic.

Now, legs. Legs are interesting. First of all, your robot will need to be
strong enough to carry its own weight, plus some extra strength for inertia.
That means servomotors with enough torque, and a battery with low enough
internal resistance to power them. If you want anything better than the silly
chopstick walkers, or the ridiculous bipedals with huge feet, you will also
need a lot of those servomotors. At least three per leg, to have full inverse
kinematics. Multiply that with the number of legs, from four to eight, and you
you get from 12 to 24 servomotors. Expensive and power-hungry, but that's the
price of awesomeness! You can improve the situation a little by initializing
the servomotors in a sequence, not all at once, and by adding a large capacitor
next to the battery -- that will smoothen out any spikes in power consumption.
Of course you won't connect all those servomotors to your central unit
directly, it doesn't even have so many pins. You will need a servo controller,
and you will need to send the commands to it through the serial interface or
I²C, depending on what you get. You can even make your own out of an Arduino,
especially if you need some custom functionality.

Now, suppose you have all the parts, and you start assembling it all together.
It's easy to just glue everything together and solder all the wires. But
then you realize, that you attached one of the legs up-side down, one of the
servomotors is fried and you need a larger capacitor. So you have to break it
all apart again. What a pain! Better to use gold pins, plugs, screws, and even
velcro tape. This way you can easily modify your prototype and replace parts.
Oh, and by the way, have some spares on hand. They *will* break. That's how
the physical world works.

As for software, it's in equal parts programming and system administration.
Remember that this is practically a mobile data center -- multiple electronic
devices communicating with each other. For instance, to use the serial
interface you will need to edit `/boot/cmdline.txt` and `/etc/inittab` to
disable the system console that normally runs there. And to use I²C, you will
need to comment out the blacklisted modules from
`/etc/modprobe.d/raspi-blacklist.conf`, and so on. Even if your program doesn't
need any fancy settings or permissions, you will still need to make it run at
system startup, or have some other way to start it.

I won't write much about the actual code here. After all, you are a programmer and
it's what you want to solve by yourself. Just a few hints. Look for "inverse
kinematics" -- that's what you will need to translate the coordinates of the
leg tips into actual servomotor angles. And the position of the robot's body
into the positions of individual legs. Then, remember that animating a physical
thing is very similar to animating computer graphics -- just instead of writing
pixels to the screen, you are sending commands to the servos. You are on your
own with the rest.

Controlling your robot can also be a challenge. You might try to go fully
autonomous, give it a lot of sensors, connected over ISP, I²C, 1Wire, TTL, USB
or even directly to the pins as analog input. There is a wide range of sensors
available, from proximity (both sonar and light-based) and motion sensors,
through light, color, temperature, ambient noise, touch, acceleration,
direction, GPS, to moisture.  You can even have a camera and use OpenCV for
image analysis! However, it's nice to have some kind of manual override. You
can use a WiFi dongle and simply SSH to it. Or get one of those wireless game
pads. Just remember that the Sony Sixaxis controller is not supported very
well, especially if it's not the original one. You could even have your
computer talk to your robot through a Bluetooth or IRDA or one of those
transmitter-receiver sets for Arduino.  Whatever you choose, make sure it's
always possible to just connect a good old monitor screen and keyboard to it,
in case something goes very wrong and you lose access.

Finally, there is the equipment that your robot will carry. Of course, crawling
around and trampling enemies is cool in itself, but you can make it even
better. A speaker for making beeps or playing the `DESTROY.wav` file over and
over (remember to get a small audio amplifier too, so that it can be heard).
Blinking LEDs. A nerf rocket turret. Maybe even an Airsoft gun, so that you can
take part in a Mech Warfare contest?

Last, but not least, remember about your own safety. Conquering the world is so
much harder when you have no hands and you are bleeding from your eyes. Don't
look into lasers, don't use power tools without glasses, don't play with high
voltages, always be careful which end of the soldering iron you are grabbing.
And remember that the LiPo batteries will erupt in flames if you so much as
look funny at them. Seriously, search YouTube for videos of burning LiPos. You
don't want that to happen in your secret lair. And never shoot anything at
humans -- you don't want them to become suspicious before your plans are fully
prepared!

Now go forth and create robots! It's great fun. It's also addictive, expensive
and takes all your free time -- a perfect hobby.


<!-- Przeczytane: Kuba Janoszek -->
