# NotSoBasicArduino
 The follwing files are my second foray into Arduino
 
 
## Table of Contents
* [Table of Contents](#TableOfContents)
* [LED_Fade](#LED_Fade)
* [HelloFunctions](#HelloFunctions)
* [NewPing](#NewPing)
---

## LED_Fade

### Description & Code
For this Assigment - We started off by making an LED blink, and then we tweaked the code just a bit to make it fade.

```C++
  analogWrite(led, brightness);

  // change the brightness for next time through the loop:
  brightness = brightness + fadeAmount;

  // reverse the direction of the fading at the ends of the fade:
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
```
In this LED fade assignment, we started using a slightly different code function. We use **analogWrite**. It helps us change the brightness of the LED. We tell the computer where our led is, and then set the brightness. By using the if statement, we tell the computer the "zone" of fading that it is allowed in so that it keeps on bouncing back and forth between the 2 numbers - 0 & 255. 
### Evidence
[LED Fade on Arduino Create](https://create.arduino.cc/editor/sypr45/5096f478-9a18-404d-8190-0ddfa59e87c8/preview)

### Images

<img src="Images/LEDFade.png" alt="LEDFade" width="500" height="400">

### Reflection

This assignent was more of review from last year. It was simple, I just had to read a bit about the analogWrite function from the [Article](https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/) on the Arduino Website, because I forgot.

## HelloFunctions

### Description & Code

In this assignment, I had to make an ultrasonic sensor read distance and move a servo according to the servo. Easy right? NO, but Yes. We weren't allowed to use the NewPing library, and we had to use a new concept called functions to write our code. Functions aren't that complex. Instead of having 20 lines of code to do something super complicating, you would only need to writ 1 line of code(but that 20 lines of code is still there, it's just to the side so it dosen't get too confusing).

Here's how you make code look like code:

```C++
void getDistance(int trigPin, int echoPin ) {
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  // Trigger the sensor by setting the trigPin high for 10 microseconds:
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  // Read the echoPin, pulseIn() returns the duration (length of the pulse) in microseconds:
  duration = pulseIn(echoPin, HIGH);
  // Calculate the distance:
  distance = duration * 0.034 / 2;
  // Print the distance on the Serial Monitor (Ctrl+Shift+M):
  //Serial.print("Distance = ");
  //Serial.print(distance);
  //Serial.println(" cm");
  delay(50);
}
```
**FYI - This is my function code** All this code does is that it tells the sensor to turn off, then turn on, then off again. By doing this it creates a wave so it bounces of the nearest sensed object and comes back(that's how ultrasonic sound/waves work. FUN Fact - Dolphins use the same techinique to find food). Then, it takes the amount of time it took for the wave to come back, and converts it to **distance** with a simple formula(distance = duration * 0.034/2;). Now that I got the distance, I had to see how to get it to work as a function. You see where it says **void distance(...)** in the code? That's all you need to use a function. Use **void** and then next to it put whatever you want to name your function(I named mine getDistance, but it could even be cookie). put your long code in the {...} of the void function and you're done. When writing the code you will be looking at, just write your function name(DON'T WRITE VOID), and it would work. **Here's what my final code looked like**(I had another function called servoFunction to move the servo).

```C++
void setup() {
  // Define inputs and outputs:
 
  myservo.attach(4);
  //Begin Serial communication at a baudrate of 9600:
  Serial.begin(9600);
}
void loop() {

  getDistance(2,3);
  //Sends ultrasonic wave to object and records distance

  if (distance > 100) {
    servoFunction(180);
    //moves servo clockwise
  }
  else {
    servoFunction(0);
    //moves servo anti-clockwise
  }
}
```

### Evidence

[HelloFunctions on Arduino Create](https://create.arduino.cc/editor/sypr45/b6ea4a67-0f89-489c-891d-af50d6261f63/preview)


### Images

<img src="Images/HelloFunctions.png" alt="HelloFunctions" width="500" height="400">

### Reflection

It was a new assignment to me, but it was still very simple. The main thing to remember is to not try and overthink anything. If you just read and follow the instructions, it will be easy. ALSO, when writing your functions make sure to add () at the end of it. I took a long time trying to figure out why my code was not running according to plan b/c I forgot to add ().

## NewPing

### Description & Code

In this adventure into Arduino, we explore the NewPing library. Funny thing is... a library is a space with a million functions in it. So... you really never need to do all that code that we did in the last assignment to make an ultrasonic sensor function. Functions are still very heandy especially when your working on a custom project, and you're repeating the same chunk of code 20 times in your code. Anyway, hats off to Tim Eckel - He made the Newping library so we don't have to spend 5 hours making an ulrasonic sensor do something. When we use a library, we mention it at the top of our code, and whenever we need to use something from that library, we call the specific function that we want. As far as wiring 2 pins go to **Power and GND**, and 2 go to pins on the board.

Here's how you make code look like code:

```C++
#include <NewPing.h>
int trigPin = 2;
int echoPin = 4;
NewPing sensor1(trigPin, echoPin, 200);
int distance; 

void setup() {
    pinMode (trigPin, OUTPUT);
    pinMode (echoPin, INPUT);
    myservo.attach(7);
    Serial.begin(9600);
}

void loop() {
   distance = sensor1.ping_cm();
     Serial.println("Distance = ")
     Serial.println(distance);
```
Talk about how the code works, here....

### Evidence

[NewPing on Arduino Create](https://create.arduino.cc/editor/sypr45/c47be415-c295-44e4-ad8b-d86bdb5a99ff/preview)

### Images

<img src="Images/NewPing.png" alt="NewPing" width="500" height="400">

### Reflection

Once you understand what the use of a library is, and ho helpful it is, you will probably be using a library in every project you do. Some people have made libraries with HUNDREDS of lines of code, so we can just use that! The only thing is that it is important to know what you're doing instead of just copying and pasting libraries and functions.
