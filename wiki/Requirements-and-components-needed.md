## Requirements

Generally speaking, an all sky camera should have the following requirements:

- it needs to record as much of the sky as possible, with as much details as possible
- it should have a light sensitive camera so it works in very low light conditions
- it should be autonomous
- it should be weather proof
- it should be remotely accessible

## Components needed - shopping list

For a complete all sky camera setup that is autonomous and permanently placed outside, you would roughly need the following components:

- A Raspberry [Pi 4B](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) or [Pi 5](https://www.raspberrypi.com/products/raspberry-pi-5/)
- [a SkyCamOne HAT](https://titanastro.com/store/SkyCamOne-HATs-c173503509)
- a camera with [lens](https://titanastro.com/store/1-2-1-55mm-F2-0-IR-CS-mount-fisheye-lens-185-degree-FoV-p728243754)
- a weatherproof housing
- a [transparent dome](https://titanastro.com/store/Dome-4-diameter-CCTV-clear-acrylic-p698624616)
- a power supply
- a [dew heater](https://titanastro.com/store/Dew-heaters-c176908335)
- an [environment sensor](https://titanastro.com/store/Temphum-sensor-SHT31D-I2C-QWIIC-p692557720) and [cable](https://titanastro.com/store/QWIIC-I2C-Sensor-connection-Cable-p692223382)

Optionally, you could equip your camera with a focus mechanism. For this you would need some additional items:

- a [stepper motor](https://titanastro.com/store/28BYJ48-5V-Stepper-motor-p692220361) and a [belt and pulley set](https://titanastro.com/store/GT2-Focus-Kit-Pulleys-and-belt-p696697425)
- some sort of mounting of the motor to the lens

And lastly, you could use a dome cover to protect your dome and camera from the sun during the day or from rain. For that, you would need:

- a [servo motor](https://titanastro.com/store/SG90-Micro-Servo-p692218128)
- some sort of dome cover

We’ll discuss these components in more detail below.

### Raspberry Pi

The Raspberry Pi is a so-called small Single-Board Computer (SBC), the heart of your all sky system. It runs the software and your camera will be connected to it. The Pi will be recording the images from the camera and will take care of creating your time-lapse videos, keograms, startrails and images.

Many people choose the [Raspberry Pi 4B](https://www.raspberrypi.com/products/raspberry-pi-4-model-b/) since it is a very dependable mini-computer with a relatively low power consumption.

However, the [Raspberry Pi 5](https://www.raspberrypi.com/products/raspberry-pi-5/) in combination with a [Titan Astro SkyCamOne HAT](https://titanastro.com/store/SkyCamOne-HATs-c173503509) will make it possible to use NVMe memory device in the form of an M.2 SSD drive. These drives are fast, very reliable and have large storage capacity. If you require this for your build, the [Pi 5](https://www.raspberrypi.com/products/raspberry-pi-5/) is the way to go.

### SkyCamOne HAT

<img src="https://i0.wp.com/titanastro.com/wp-content/uploads/2025/01/RPi_HAT_5_Rev.C_2025_v1_2025-Jan-19_10-36-11AM-000_CustomizedView6076636816_png_alpha.png?fit=300%2C169&ssl=1" style="zoom:33%;" />

HAT stands for **Hardware Attached on Top** and in this case it refers to the fact that the [SkyCamOne cards](https://titanastro.com/store/SkyCamOne-HATs-c173503509) attach on top of a Raspberry Pi 4B or 5 like in the adjacent picture.

The SkyCamOne HATs work as an **extra layer of hardware** to the Raspberry Pi, enabling the Raspberry Pi to **host a list of features** that we **commonly use** in all sky camera builds.

One important feature is the **power supply** circuit of the [SkyCamOne HAT](https://titanastro.com/store/SkyCamOne-HATs-c173503509). It simplifies powering the camera and different internal systems. One can power the complete camera with **just a network cable** or a **single 12 volt** cable going into the housing.

Another feature is the interface for **two stepper motors**. Stepper motors can be used to aid in **focusing** the camera or changing the **height** of our camera within the dome.

It also provides an interface for a **servo motor**, the same ones used in model cars and airplanes, which we could use to activate a dome cover for instance.

Furthermore, the [SkyCamOne HATs](https://titanastro.com/store/SkyCamOne-HATs-c173503509) have interfaces for **I2C sensors**, a **fan controller** for active cooling, a **dew heater** output and in case of the HAT for Raspberry Pi 5 an **SSD slot** for storage memory.

Using a [SkyCamOne HAT](https://titanastro.com/store/SkyCamOne-HATs-c173503509) **takes away the necessity to create custom electronic circuits**, having to debug and having to reinvent the wheel. You can directly connect your stepper motor, servo, sensors and dew heater **without** the need for **additional electronics**.





### Camera and lens

<img src="https://i0.wp.com/titanastro.com/wp-content/uploads/2025/02/Arecont_Vision_mpl1_55_1_55Mm_1_2_F2_0_Fixed_1363711102_872528.jpg?fit=300%2C300&ssl=1" alt="img" style="zoom:33%;" />

This one is a tricky combination. Depending on which camera you choose, you choose your lens. Not all cameras work well with all lenses and vice versa. 

You will also want a near horizon-to-horizon field of view for your all sky camera, and a wide angle lens just does not give the same result with a small camera sensor size as it does with a large sensor size.

A commonly used lens is the [1.55mm f2 CS mount fisheye lens](https://titanastro.com/store/1-2-1-55mm-F2-0-IR-CS-mount-fisheye-lens-185-degree-FoV-p728243754). With a 1/2″ camera sensor this lens will provide a full view of the sky with a complete image circle. However, with a 1/3″ sensor you will have an image that will be slightly clipped on the top and bottom.

Commonly used cameras are the [Raspberry Pi HQ](https://www.raspberrypi.com/products/raspberry-pi-high-quality-camera/) camera, [ZWO planetary cameras](https://www.zwoastro.com/product-category/cameras/planetary_cameras/) or [QHY cameras](https://www.qhyccd.com/planetary-camera-qhy5iii485c/).

##### **Camera simulator**

Aaron W. Morris, the author of [INDI Allsky](https://github.com/aaronwmorris/indi-allsky), has a [camera simulator](https://allsky.aarmor.net/indi-allsky/camerasimulator) built within INDI Allsky that helps you appreciate how any lens combines with different types of sensors.





### Weatherproof housing

Your electronics and camera should be **protected from the elements**. That is where the housing comes in.

Some all sky camera designs are based on a **fully closed system**. No moisture in or out, no air in or out. We believe this to be **wrong**. And we’ll try and explain why we think that.

In some environments, the **temperature** within an all sky housing during the day can **vary greatly**. From temperatures below zero degrees Celsius (32 degrees Fahrenheit) at nighttime to temperatures of over 50 degrees Celsius (122 degrees Fahrenheit) at daytime. 

In fully closed housings, this creates **significant pressure differences**, which will eventually **end up breaking seals**. It will also affect how your environment sensor reacts and **incorrectly reads** your environmental situation.

Your electronics and your camera will also **suffer** from these vast differences between night and day.

If we **open up** our enclosure to the outside environment in a **controlled manner** and we introduce a **fan to circulate the air** within the housing, we have a much better control of the temperatures inside the housing and we **eliminate the pressure differences**. Additionally, we will have a **better ‘feel’** with the outside environment from our environment sensor.

To connect your waterproof setup via PoE, we can recommend using an [IP68 rated ethernet panel connector](https://titanastro.com/store/IP68-CAT6-Waterproof-Panel-Connector-p728229377).



### Transparent dome



To protect your camera from the elements but still provide good visibility with a minimum of distortion, we use transparent domes.

Usually, the type of dome you see on your local supermarket ceiling, with a CCTV camera in it. 

In most cases, a 3″ or [4″ diameter dome](https://titanastro.com/store/Dome-4-diameter-CCTV-clear-acrylic-p698624616) is used. The lens of your camera should be placed just **above** the **center** of your dome to minimize optical distortions from the extrusion of the acrylic.

<img src="https://i0.wp.com/titanastro.com/wp-content/uploads/2025/02/Lens-placement.webp?fit=1024%2C477&ssl=1" alt="img" style="zoom:33%;" />

High end cameras use silicon (glass) domes with an Anti-Reflective (AR) coating on the inside. These are costly and because most do not have a flange they are harder to mount and keep sealed.





### Dew heater

Your camera sits under the **protective acrylic or glass dome**. It **protects your camera** from the elements, from sand and dust in the air, from bird droppings, you name it.

Unfortunately, in most environments it also introduces a problem: **dew**.

Dew is actually **moisture in the air** that condenses on relatively cold surfaces under certain circumstances. These circumstances include favorable values for air temperature and relative humidity of this same air.

The **formula** for this, as proposed by Mark G. Lawrence is as follows:
$$
Td = T - ((100 - RH)/5)
$$
Td is the dew point (temperature), T is the temperature and RH is the Relative Humidity.

So, if the relative humidity of the air surrounding my camera is 68% and the temperature is 15 degrees Celsius, then the dew point is 15 – (100 – 68)/5 or 15 – 32/5 = 8,6 degrees Celsius.

So, whenever we reach 8,6 degrees Celsius, we can expect **dew to form on anything**. We can **mitigate** this by just **making sure we do not reach** 8,6 degrees Celsius. How, you ask? By **heating up!**

We can place a so called **dew heater inside our dome**. A dew heater is generally an **array of** small **resistors** that heat up when current runs through them. This maintains the air in that dome nice and warm, or at least well above the dew point temperature. By doing that, we will **not have any dew** in our dome and we’ll have good views of the sky all the time.

Another advantage of a dew heater is that it will help us **dry up rain drops** faster and will also help **melt snow** or hail that has fallen on our dome and obstructs our view.

 



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



### Environment sensor and cable

<img src="https://d2j6dbq0eux0bg.cloudfront.net/images/100555537/4744540326.png" style="zoom: 25%;" />

In order for your all sky system to know what the environment is doing as far as temperature and humidity go, we need some sort of sensor. With the SkyCamOne HATs you can use any type of I2C sensor. A very reliable sensor that is protected from the adverse effects of moisture, is the [SHT31-D](https://titanastro.com/store/Temphum-sensor-SHT31D-I2C-QWIIC-p692557720). This sensor measures temperature and humidity with a very high precision and even has a built-in heater!

Other sensors that work well are the BME280 or BME680.

Most of these sensors nowadays use a standard cable called a [QWIIC-cable](https://titanastro.com/store/QWIIC-I2C-Sensor-connection-Cable-p692223382). These are used by many sensor manufacturers including SparkFun and AdaFruit, but they are also the standard cable used by the SkyCamOne HATs.



### Stepper motor and belt and pulley set

If you are planning on building a system which enables you to remotely focus your camera or even use some sort of autofocus solution, you will need a way to turn your lens (that's how you focus, by turning your lens and actually screwing it further in or further out).

A very reliable way of doing this is with the help of a [stepper motor](https://titanastro.com/store/28BYJ48-5V-Stepper-motor-p692220361). A stepper motor is not a regular electric motor, but a motor which moves in predefined small steps. The great advantage is that we can count the steps in one direction and return to our starting position by executing the same amount of steps in the opposite direction. 

In our experience we have found that the most reliable and precise manner of connecting this stepper motor to your lens is with a [belt and pulleys](https://titanastro.com/store/GT2-Focus-Kit-Pulleys-and-belt-p696697425). This further reduces the steps of the stepper motor for additional precision, is easy to install and durable.

As with any mechanical moving system, our belt and pulley solution has backlash. Backlash is the 'free play' in the mechanical setup, in the sense that no mechanical connection is 100% accurate. To illustrate: as we move our lens in one direction a few dozens of steps and next we decide we need to move in the other direction, it will take a determined number of steps before the lens actually starts to move in the opposite direction. This is because there is a little bit of space between the teeth of the pulleys and the belt, because the belt might be a bit loose or any number of reasons. This is not a problem, most of the times. We can simply count the number of steps we need to do before the lens starts moving again and record this number. We'll call this the steps needed to get out of the backlash and we can tell our software to remember that backlash and apply these extra steps each time we change the direction of movement of our lens.

### Motor mount

<img src="https://titanastro.com/wp-content/uploads/2025/03/Screenshot-2025-03-04-132041.jpg" style="zoom:33%;" />

For the stepper motor and bulley and pelt (ok, I know it's pulley and belt) system to correctly fit with the camera, some sort of motor mount is needed. This is actually pretty simple to make.

If you use the GT2 pulley and belt kit, the optimal distance between the pulleys from center to center is 38mm.

For your convenience, there is a [mounting plate design](https://github.com/TitanAstro/3D-Resources/raw/refs/heads/main/Stepper%20Mounting%20plate.step) on our GitHub which you can make from virtually anything: wood, a sheet of plastic, sheet metal or 3D printed.  This mounting plate is designed to fit around a ZWO camera (51mm diameter) and the [**28BYJ48** stepper motor](https://titanastro.com/store/28BYJ48-5V-Stepper-motor-p692220361).

### Servo motor and dome cover

A servo motor is another type of positional actuator. Normally servo motors have a range of motion of around 180 degrees. They are usually very lightweight and strong because of the way the internal mechanism is designed. Servos work with a simple PWM (Pulse Width Modulation) signal, which your SkyCamOne HAT provides through the servo connector.

A servo is perfect for a dome cover, in particular for the clamshell type dome covers. The below design is by Wichie Rivera.

<img src="https://titanastro.com/wp-content/uploads/2025/03/Screenshot-2025-03-04-121532.jpg" style="zoom:33%;" alt="Beautiful design by Wichie Rivera"/>

