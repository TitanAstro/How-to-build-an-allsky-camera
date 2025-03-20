### Power supply

The next item on your list is some sort of **power supply**. 

You need power for your Raspberry Pi, your camera, your dew heater and fan, and for your sensors. Possibly also for your stepper, servo and what more.

This can easily amount **up to 25 Watts**. That does not seem a lot, but it actually is.

With a [SkyCamOne HAT](https://titanastro.com/store/SkyCamOne-HATs-c173503509) in your system, you have **two** preferred **ways** of powering everything: **via a network cable or with a power adapter**.

The advantage of powering via a network cable is that you have a very stable network connection and power all via one single cable into your housing. Power via the network cable is called Power over Ethernet or PoE for short.

You can buy a **PoE network switch** or a so called **PoE-injector** which is basically a transformer.

The other method of powering via your SkyCamOne HAT is by **supplying it with 12 Volts** with a good power supply. With a good power supply we mean one that actually can deliver some power (in the Watt-sense), since you might well be needing **25 or more Watts**.

Since the formula for power is;
$$
[ P = V x I ]
$$

$$
P (Watts) = V (Volts) x I (Amperes)
$$

then in the case of 12 Volts and your system needing 25 Watts, we can fill out the formula and state it as:
$$
P = V x I   
$$

$$
25 = 12 x I
$$

Since we would like to know the value of I, can say that *I = 25 / 12 = 2.08* Amperes. So your 12 Volt power supply needs to be able to deliver at least 2.1 Amperes. Just so you know.


