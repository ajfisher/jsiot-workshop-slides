# Workshop:<br/> Web Connected Physical things with JavaScript
<!-- .slide: class="title" -->

DDD, August 8, 2015 <!-- .element: class="location" -->

Andrew Fisher @ajfisher<!-- .element: class="author" -->

Notes:

Objective 2min
- intro to building web connected things

---

## TODO

1. Introduction to electronics & JS hardware stack
2. Building an API connected thing
3. Acquiring data from the environment

Notes:

---

## Introduction to electronics

// some sort of pic

Notes:

---

## Voltage, Current, Resistance

// Use image that is the pipes analogy

Notes:

---

## Microcontrollers

// pic of arduino

Notes:

---

## Sensors and actuators

LEDs, Servos, Motors, Temp, Buttons, Light

Notes:

---

## Resources

* Arduino Experimenters Kit (ARDX)
* Others

Notes:

---

### JS <3 Robotics
<!-- .slide: data-background="/images/robot_love.jpg" -->

(CC) Flickr <!-- .element: class="attribution" -->
[hiperbolica](https://www.flickr.com/photos/hiperbolica/3414999010)

Notes:

That's enough of talking about why JS is really well suited to working with robotics.
We all work with JavaScript and know it's a real and interesting language -
Let's move on to what the hardware stack looks like.

---

## The NodeBots stack

![](/images/logo.png)

Notes:

There are a few different projects that can use JavaScript on hardware now,
however the one we're going to talk about is called nodebots as it's very much
aimed at a NodeJS implementation with hardware. At the core of nodebots are
transport layers to deal with things like talking over USB or wireless or serial
connections and then wrapped around that is a framework called Johnny Five.

---

## Johnny Five
<!-- .slide: data-background="/images/rick.jpg" -->

(C)<!-- .element: class="attribution" -->
[Joanne Daudier](https://twitter.com/jdaudier)

Notes:

Johnny Five was started by this guy - Rick Waldron, and there are now about
30 core project members, nearly 100 contributors and over 2000
commits to the codebase in the last couple of years. It's a very active and
expanding project and we're always looking for more contributors to help out.

Johnny Five is a hardware abstraction framework so instead of writing code that
is specific to a chip you can talk about components that behave in different
ways and leave the implementation details up to the people who write the 
board level interfaces whereupon you can then use it.

---

### The stack

* Controller board (sensors and actuators)
* IO Plugin (communications protocol)
* Johnny Five / NodeJS (application logic)
* WS/HTTP (networking and security protocols)
* Clients (UI, input, visualisation)

Notes:

So this is what the typical JS hardware stack looks like. 

We have a board which could have sensors and actuators. Actuators is just a
fancy word for something that does something in the real world - like a motor
or an LED etc. Most controller boards can't run JS yet so we normally need to 
put some firmware on them to do what we want.

This talks via a communications protocol to what is called an IO Plugin. IO
plugins are a Johnny Five idea that tries to get hardware to behave in consistent
ways via a protocol. Think of this sort of like HTTP requests and responses - the
client doesn't really care what the server does as long as it responds properly.

Johnny Five gives us hardware abstraction so we can turn motors and LEDs into 
JavaScript objects and interact with them. As a side effect we get all of NodeJS
as well so that means we can start doing interesting things like linking up
with our normal web protocols. And then finally we can add clients for things
like UI, input and what not.

---

### Common implementation

* Controller board (Arduino)
* IO Plugin (Firmata over USB)
* Johnny Five / NodeJS (application logic)
* WS/HTTP (networking and security protocols)
* Clients (UI, input, visualisation)

Notes:

So in practice this is what a specific implementation of this stack looks like.
You can see we've got an arduino board in this case and the IO Plugin is 
a firmware called Firmata which provides us the interface to the board for Johnny
Five. This is about the most basic and most common stack you can use but you can
see that the bit we are concerned about - being the bit in the middle pretty
much stays the same all the time.

---

## NodeBots hardware

* Servos, Motors, ESCs, Stepper motors
* Accelerometers, Gyroscopes, Compasses, IMUs
* Temperature, Proxitimity, Pressure sensors
* LEDs, NeoPixels, Pixel matrices
* Switches, Joysticks, Buttons
* LCDs

Notes:

In terms of hardware - there is a lot covered in Johnny Five and more core
components are still being added. The intent is to have the majority of the
most common electronics components you're likely to come across available in
the framework and then you can use then to compose bigger objects that then
represent your thing that you're making.


---

### Installation 

* Board development environment (eg Arduino)
* Flash board with protocol (eg Firmata)
* npm install johnny-five
* Write code
* ...
* Make an awesome robot

Notes:

So to get up and running, it's pretty much just a case of getting the board dev
environment going. For arduino that's prerry much just download the arduino
IDE and install it. You then put the IO protocol on the board that you need - 
for an arduinon that just means using Firmata and then it's an npm install
and you are then writing code.


---

## Examples and applications
<!-- .slide: data-background="/images/np_glasses.jpg" -->

Glasses (C)<!-- .element: class="attribution" -->
[Andy Gelme](https://twitter.com/geekscape) | 
Image (CC) [Matthew Bergman](7215764961901652://www.flickr.com/photos/matthewbergman/15337663413/)

Notes:

With all this power, what sort of things can you build? Well I'm going to show
you some examples of some fun things people have made and show you some code
as well.

---

### SimpleBot
<!-- .slide: data-background="/images/simplebot.jpg" -->

Simplebot (CC)<!-- .element: class="attribution" -->
[AJ Fisher](https://twitter.com/ajfisher) 

Notes:

This is a basic teaching bot we use in Australia for nodebots events. Very
basic and allows you to explore fundamentals of robotics design and motion. It
is very cheap and fast to build so good for beginners.

---

### Node Skirt
<!-- .slide: data-background="/images/skirt.jpg" -->

Skirt (C)<!-- .element: class="attribution" -->
[Kassandra Perch](https://twitter.com/nodebotanist) | 
Image (CC) [Matthew Bergman](https://www.flickr.com/photos/matthewbergman/15969524882/in/set-72157649619016521)

Notes:

This skirt, made by Kassandra Perch is fully contained running javascript on a little board embedded into
it. It has an accelerometer and as you move around the LEDs inside it light up
different colour. So you can even use JavaScript in your clothing!!


---

### Tetris
<!-- .slide: data-background="/images/tetris.gif" -->

(C)<!-- .element: class="attribution" -->
[Adrian Catalan](https://twitter.com/ykro)

Notes:

Here is an example of using nodeJS to make a physical game. This is made by 
Adrian Catalan and uses nodebots and node-pixel to make a tetris game on
LED panels.

---

### Tharp
<!-- .slide: data-background="/images/tharp.gif" -->

(OSC)  <!-- .element: class="attribution" -->
[dtex](https://github.com/dtex/tharp)

Notes:

Donovan Buck has done a lot of work on making sophisticated animation control
in nodebots with a library to solve inverse kinematics problems. Here you 
can see he has attached a 6-leg robot to a leap motion for hand control and it
responds very very fast to his movement. 

---

### Hello World
<!-- .slide: data-background="/images/hello_world.jpg" -->

(CC) Flickr <!-- .element: class="attribution" -->
[Daniel Novta](http://www.flickr.com/photos/vanf/5210360116)

Notes:

So now you've seen some examples, let's see a demonstration. With hardware you 
most of the time don't have a screen. So a hello world example is just getting
an LED to blink on and off.

---

## Exercise 1: hello world 15 mins
- LED Circuit
- put firmata on the board
- JS example
- test

---

## Exercise 2: api connected thing (40 mins)
- outline - connect an actuator to the web called an information radiator
- discuss egs - twitter light, gmail indicator, weather forecast, sales simulator
- walk through sales example 
  - emits event when there's a sale
  - respond and light up when that happens
- highlight code for others

---

## Exercise 3: data acquisition (30 mins)
- outline - connect a sensor to the web
  - data
  - destination
- discuss egs - light and temperature sensors using phant
- walk through example of temperature sensor and logging data and visualising it.

---

## Resources

* johnny-five.io
* node-ardx.org
* nodebotsau.io


---

# Workshop:<br/> Web Connected Physical things with JavaScript
<!-- .slide: class="title" -->

DDD, August 8, 2015 <!-- .element: class="location" -->

Andrew Fisher @ajfisher<!-- .element: class="author" -->

Notes:

Objective 2min
- intro to building web connected things

