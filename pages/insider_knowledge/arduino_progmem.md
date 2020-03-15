---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Expertenwissen
description: Hier wird weiterführendes Wissen, das für die Programmierung der Arduinos nützlich ist, gesammelt.

# Author box
author:
    title: Thomas Seidler
    title_url:
    external_url: true
    description:

# Micro navigation
micro_nav: true

---

# Arduino Speichermanagement

Auf dem Arduino hast du Zugriff auf drei verschiedene Arten internen Speicher: 

 - Flash Speicher: Hier werden das eigentliche Programm und der Bootloader gespeichert. Das heißt, dass hier der Sketch, den du in der IDE erstellst, gespeichert wird.
 - SRAM (static random access memory): Hier werden dynamische Variablen, die bei der Ausführung des Programms gebraucht werden, gespeichert. Dieser Speicher wird bei Unterbrechung der Stromzufuhr überschrieben. Wenn du also in deinem Programm eine Variable definierst (das kann eine einfache Zahl, aber auch eine ganze Matrix oder ein beliebiges Objekt sein), wird diese im SRAM gespeichert.
 - EEPROM: Hier kann Information gespeichert werden, die längerfristig benötigt wird. Du kannst hier also z.B. Bilder (Matrizen) speichern, die du auch nach Unterbrechung der Stromzufuhr zum Arduino weiter verwenden möchtest.

Auf dem Arduino Uno ist folgender Speicherplatz vorhanden:

 - Flash: 32 kB
 - SRAM: 2kB
 - EEPROM: 1kB

Wenn du mehrere Matrizen samt rgb Werten (Farben) speichern möchtest, kann es passieren, dass der SRAM zu klein für alle Variablen ist. Du solltest daher alle Variablen im kleinstmöglichen Datentyp abspeichern.
Darüber hinaus kannst du statische Variablen, also solche, deren Wert sich während der Ausführung der Programms nicht ändert, in den Flash Speicher schreiben. Dazu musst du das PROGMEM keyword verwenden:

```c
#include <avr/pgmspace.h>

const dataType variableName[] PROGMEM = {data0, data1, data3…​};

void setup(){
...
}

void loop(){
...
}
```

Mehr unter [https://www.arduino.cc/en/tutorial/memory]('https://www.arduino.cc/en/tutorial/memory').
