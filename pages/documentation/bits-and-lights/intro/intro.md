---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Bits & Lights
description: Wir fangen ganz einfach an und programmieren ein bisschen Licht auf eine LED-Matrix. Im Hintergrund haben wir ein bisschen was vorbereitet, sodass du mit ein paar ganz einfachen Zeilen Code deine ersten Bilder und Licht-Animationen auf deiner LED-Matrix siehst.
hero_image_url: /pages/documentation/bits-and-lights/intro/rainbow.jpg

# Author box
author:
    title: Christoph Burnicki
    title_url: 
    external_url: true
    description: 

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
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

```c
void showMonochromeArray(bool leds[16][16], int r, int g, int b) {
  for (int i = 0; i < 16; i++) {
    for (int j = 0; j < 16; j++) {
      if (leds[i][j]) {
        light(i, j, r, g, b);
      } else {
        light(i, j, 0, 0, 0);
      }
    }
  }
  pixels.show();
}

void light(int row, int column, int r, int g, int b) {
  int i;
  if (row%2 == 0) {
    i = (row * 16) + (15 - column);
  } else {
    i = (row * 16) + column;
  }
  pixels.setPixelColor(i, pixels.Color(r ,g, b));
}
```
