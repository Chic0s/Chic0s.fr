---
title: "Keyboard with RubberDucky"
date: 2023-11-12T16:44:42+01:00
draft: false
categories: "Physical Pentest"
tags: ["pentest", "hardware", "ATtiny85"]
---

# Integration of a Rubber Ducky into a USB Keyboard

Objective: We are increasingly faced with the presence of dangerous USB keys. However, keyboards can also be a means of injecting malicious code into your computer. We will see how to create a keyboard with a Rubber Ducky. Nevertheless, for security reasons, no code will be disclosed.

## Hardware

Firstly, a soldering set will be necessary, and you need some basic skills to complete this project.

A small soldering iron (Be cautious about the wattage to avoid damaging the equipment)
Some spare cables
Solder
One or more spare USB-A female connectors
A nice website to find the necessary equipment: https://www.e44.com/

Nothing better than a quick look on Amazon to find what we need!
We need some items to complete our project 🙂:

A USB keyboard
A USB hub
An ATtiny85
Here's a picture of the shopping list:

![targets](/img/list.png)

A total of €27.97.

## Schema and Soldering

Let's start our project.

The first objective is to disassemble the keyboard to see what's inside.
![targets](/img/carte.jpg)
Inside, we find the circuit board that controls the keyboard.

The second objective is to disassemble the USB hub to see what's inside.

Finally, let's create a neat schematic for our soldering and testing!
![targets](/img/schema.png)

You may suspect that it's not that simple, right? Well, despite my basic level in electronics, I was able to create a keyboard containing an ATtiny.

In my case, I used the USB-A female connector provided with the hub to keep costs down.
![targets](/img/soudure.jpg)

However, I will need to buy another one because the provided one does not meet my expectations. The dimensions are too large and do not allow the system to be hidden properly.

Here is the schematic of a USB-A female connector:
![targets](/img/usbA.png)

A slight modification to avoid a bulging external appearance on the keyboard.
![targets](/img/end.jpg)

As mentioned earlier, for security reasons, I will not provide any code. It's up to you to do your research.

It is essential to use this project in an educational context or to raise awareness.
