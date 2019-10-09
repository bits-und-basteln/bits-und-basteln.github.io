---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Wann und Wo?
description: Page description
hero_image_url: /pages/info/beusselstrasse-header.jpg

# Author box
author:
    title: Christoph Burnicki
    title_url: 
    external_url: true
    description: 

# Micro navigation
micro_nav: true

---

# Los geht's

## Hardware Setup


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



