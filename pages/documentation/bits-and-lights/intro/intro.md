---
# Page settings
layout: default
keywords:
comments: true

# Hero section
title: Bits & Lights
description: Wir fangen ganz einfach an und programmieren ein bisschen Licht auf eine LED-Matrix. Im Hintergrund haben wir ein bisschen was vorbereitet, sodass du mit ein paar ganz einfachen Zeilen Code deine ersten Bilder und Licht-Animationen auf deiner LED-Matrix siehst.
hero_image_url: /pages/documentation/bits-and-lights/intro/rainbow.jpg

# Micro navigation
micro_nav: true
---

# Los geht's

## Was wir machen wollen

Um Licht auf unsere LED-Matrix zu bekommen, brauchen wir neben der Matrix noch einen Arduino. Der Arduino ist ein kleiner Computer (Microcontroller), auf den wir nachher unseren Code laden. Der Arduino führt unser Programm aus und steuert damit die Lichter auf der LED-Matrix.

## Die Hardware

<a href="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" target="_blank"><img src="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" class="inline" alt="Der Aufbau mit Arduino und LED-Matrix"/></a>In diesem Bild siehst, du, wie der Arduino und die LED-Matrix zusammengesteckt und mit dem Netzteil verbunden werden.

**Wichtig: Bitte immer erst alles ordentlich zusammenstecken, bevor du das Netzteil in an den Strom anschliesst!**

## Der Editor (Arduino Create)

Normalerweise kann ein Programm in jedem beliebigen Texteditor geschrieben werden. Das ist manchmal allerdings etwas umständlich, deshalb gibt es extra für das Schreiben von Code ausgelegte Editoren. Einen solchen stellt auch das Arduino-Team für uns bereit. Damit lässt sich der Code sehr einfach auf den Arduino laden. Außerdem läuft der Editor online im Browser, so dass du nur ein Browser-Plugin installieren musst um loszulegen.

Den Web-Editor findest du unter [https://create.arduino.cc](https://create.arduino.cc/) -> *Arduino Web Editor*. 

Hier kannst du entweder einen neuen Account erstellen, oder dich mit deinem Google-Account anmelden.

[Aktuelle Version der Bits&Basteln Code Library](/downloads/lib_bub.zip)

**Lib.h**
```c
#ifndef Lib_h
#define Lib_h

#include <BitsUndBasteln.h>

Canvas canvas;
Ghost ghost;
Hat hat;

void drawGhost(int x, int y, long color) {
    canvas.draw(&ghost, x, y, color);
}

void drawHat(int x, int y, long color) {
    canvas.draw(&hat, x, y, color);
}

#endif
```

**intro.ino**
```c
#include "Lib.h"

void setup(){};

long GHOST_COLOR = WHITE;
long HAT_COLOR = MAGENTA;
long EYE_COLOR = 0xcc0000;

void loop(){
    canvas.clear();
    drawGhost(5, 6, GHOST_COLOR);
    drawHat(4, 4, HAT_COLOR);
    canvas.show();
    delay(500);
};

```