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

Arduinos haben drei verschiedene Sorten internen Speicher: 

 - Flash Speicher: Hier werden das eigentliche Programm und der Bootloader gespeichert.
 - SRAM (static random access memory): Hier werden dynamische Variablen, die bei der Ausführung des Programms gebraucht werden, gespeichert. Dieser Speicher wird bei Unterbrechung der Stromzufuhr überschrieben.
 - EEPROM: Hier kann Information gespeichert werden, die längerfristig benötigt wird.

Auf dem Arduino Uno ist folgender Speicherplatz vorhanden:

 - Flash: 32 kB
 - SRAM: 2kB
 - EEPROM: 1kB

Wenn mehrere Matrizen samt rgb Werten gespeichert werden sollen, kann es passieren, dass der SRAM zu klein für alle Variablen ist. Alle Variablen sollten deswegen als der  kleinstmögliche Datentyp gespeichert werden.
Darüber hinaus können statische Variablen in den Flash Speicher geschrieben werden. Dazu muss das PROGMEM keyword verwendet werden.

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
