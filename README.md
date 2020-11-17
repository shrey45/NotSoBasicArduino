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

### Reflection

This assignent was more of review from last year. It was simple, I just had to read a bit about the analogWrite function from the [Article](https://www.arduino.cc/reference/en/language/functions/analog-io/analogwrite/) on the Arduino Website, because I forgot.

## HelloFunctions

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

## NewPing

### Description & Code
Description goes here

Here's how you make code look like code:

```C++
Code goes here
```
Talk about how the code works, here....

### Evidence
link goes here

### Images
draw it yourself, take a picture, make a fritzing, whatever you want to EFFECTIVELY communicate how its put together.

### Reflection

