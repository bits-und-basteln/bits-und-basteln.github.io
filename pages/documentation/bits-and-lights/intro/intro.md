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

# Vorbereitung

## Was wir machen wollen

Um Licht auf unsere LED-Matrix zu bekommen, brauchen wir neben der Matrix noch einen Arduino. Der Arduino ist ein kleiner Computer (Microcontroller), auf den wir nachher unseren Code laden. Der Arduino führt unser Programm aus und steuert damit die Lichter auf der LED-Matrix.

## Die Hardware

<a href="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" target="_blank"><img src="/pages/documentation/bits-and-lights/intro/arduino-led-hardware-setup.jpg" class="inline" alt="Der Aufbau mit Arduino und LED-Matrix"/></a>In diesem Bild siehst, du, wie der Arduino und die LED-Matrix zusammengesteckt und mit dem Netzteil verbunden werden.

**Wichtig: Bitte immer erst alles ordentlich zusammenstecken, bevor du das Netzteil an den Strom anschliesst!**

## Der Editor (Arduino Create)

Normalerweise kann ein Programm in jedem beliebigen Texteditor geschrieben werden. Das ist manchmal allerdings etwas umständlich, deshalb gibt es extra für das Schreiben von Code ausgelegte Editoren. Einen solchen stellt auch das Arduino-Team für uns bereit. Damit lässt sich der Code sehr einfach auf den Arduino laden. Außerdem läuft der Editor online im Browser, so dass du nur ein Browser-Plugin installieren musst um loszulegen.

Den Web-Editor findest du unter [https://create.arduino.cc](https://create.arduino.cc/) -> *Arduino Web Editor*. 

Hier kannst du entweder einen neuen Account erstellen, oder dich mit deinem Google-Account anmelden.

## Code von uns für euch

Sobald sich der Editor geöffnet hat, musst du erst etwas von uns bereitgestellten Code hochladen, bevor du starten kannst. Um dir das Leben einfacher zu machen, haben wir schon etwas Code geschrieben, den du benutzen kannst. Solche Code-Pakete nennt man Bibliothek oder Library.
Lade dir unsere [Aktuelle Version der Bits&Basteln Code Library](/downloads/BitsUndBasteln.zip) herunter und füge sie im Editor unter eigenen Libraries hinzu.

In deinem Editor siehst du unter *Sketchbooks* zwei offene Tabs: Dein eigentliches Sketchbook, das die Code-Bausteine `setup()` und `loop()` enthält. Und einen `ReadMe.adoc`-Tab, den wir erstmal ignorieren können.

Erstelle einen neuen Tab, nenne ihn `Lib.h` und kopiere den untenstehenden Code hinein. Es ist wichtig, dass der Tab den kompletten untenstehenden Code und nichts sonst enthält. Der Code in `Lib.h` ist auch eine kleine Hilfestellung von uns.

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

# Los geht's mit einem Geist mit Hut

Als letzten Teil der Vorbereitung, kopiere den untenstehenden Code in deinen Sketch-Tab. Auch hier ist es wichtig, dass du den existierenden Code im Tab vorher löschst.

**intro.ino**
```c
#include "Lib.h"

void setup(){};

long GHOST_COLOR = WHITE;
long HAT_COLOR = MAGENTA;
long EYE_COLOR = 0xcc0000;

void loop(){
    canvas.clear();
    canvas.pixel(1, 1, WHITE);
    drawGhost(5, 6, GHOST_COLOR);
    drawHat(4, 4, HAT_COLOR);
    canvas.show();
    delay(500);
};

```

## Was bedeutet das?

Am Ende des Tages sollen Lichter auf der LED-Matrix in verschiedenen Farben leuchten. Dafür müssen wir dem Arduino zunächst sagen, welche Pixel in welchen Farben leuchten sollen. Jeder Pixel auf der LED-Matrix hat eine X- und eine Y-Koordinate. Um einen einzelnen Pixel an der Position `x=2, y=2` weiß leuchten zu lassen, wird der Pixel z.B. mit dem Befehl `canvas.pixel(2, 2, WHITE)` angesteuert.

Um etwas auf der LED-Matrix anzuzeigen sind allerdings zwei Schritte nötig:

1) Zuerst müssen alle Befehle ausgeführt werden, die festlegen, was angezeigt werden soll. Z.B. mit `canvas.pixel(2, 2, WHITE)` oder mit `drawGhost(5, 6, GHOST_COLOR)`.

2) Im Anschluss muss noch einmal `canvas.show()` aufgerufen werden um alle vorher auf die LED-Matrix *gezeichneten* Punkte auch wirklich anzuzeigen.

Sehen wir uns mal an, was die einzelnen Zeilen des Code-Beispiels oben bedeuten. Interessant ist erstmal nur, was auf deinem Sketch in dem `loop(){}`-Block steht. Alles, was in den Klammern hinter `loop(){` steht wird von oben nach unten in einer Schleife immer wieder ausgeführt.

Die erste Zeile, `canvas.clear()`, schaltet alle LEDs aus. Das ist in gewisser Weise das Gegenteil von `canvas.show()`. In den nächsten drei Zeilen werden Dinge auf die LED-Matrix gezeichnet: Ein einzelner Pixel an der Stelle `(1,1)` in der Farbe `WHITE`, ein Geist an der Stelle `(5,6)` in der Farbe `GHOST_COLOR` und ein Hut an der Stelle `(4,4)` in der Farbe `HAT_COLOR`.

Im Anschluss wird `canvas.show()` aufgerufen um das gezeichnete anzuzeigen. Der letzte Befehl, `delay(500)`, lässt das Programm 500 Millisekunden (= eine halbe Sekunde) warten, bevor die Schleife wieder oben im `loop()` anfängt und die Abfolge der Befehle wiederholt.
