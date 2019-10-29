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

<a href="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" target="_blank"><img src="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" class="inline" alt="Der Aufbau mit Arduino und LED-Matrix"/></a>In diesem Bild siehst, du, wie der Arduino und die LED-Matrix zusammengesteckt und mit dem Netzteil verbunden werden.

**Wichtig: Bitte immer erst alles ordentlich zusammenstecken, bevor du das Netzteil in an den Strom anschliesst!**

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
