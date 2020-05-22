# **PATRONES DE DISEÑO**

## Sections

- [Patrones_Creacionales](#PATRONES-CREACIONALES)

    -*[1.AbstractFactrory](#1.-Abstract-Factory)*

    -*[1.1Estuctura](#1.1-Estructura)*

    -*[1.2Código](#1.2-Código)*





## **PATRONES CREACIONALES** 

<div style="text-align: center">

##  **1. Abstract Factory**

> "Abstract Factory es un patrón de diseño que permite crear familias de objetos relacionados sin especificar sus clases concretas".

___

##  **1.1 Estructura**

![Abstract Factory UML](AbstractFactory.jpg )


## **1.2 Código**
</div>


~~~ python

import random
from Logic.Mariachi import Mariachi


class Band:

    listMariachi = []
    listInstrument = []
    listInstrumentTune=[]
    listInstrumentPlay=[]
    instrument = None

    def assignBand(self):
        """Asigna objetos :Mariachi() en la lista"""
        self.listInstrument.clear()
        numRandom = random.randint(5, 10)
        for i in range(0, numRandom):
            self.listMariachi.append(Mariachi())
            self.listInstrument.append(self.listMariachi[i].assignInstrument(
                random.randint(0, 4)))
        return self.listInstrument

    def tuneBand(self):
        """Recorre los objetos de la lista y los afina"""
        self.listInstrumentTune.clear()
        for i in range(0, len(self.listMariachi)):
            self.listInstrumentTune.append(self.listMariachi[i].tuneInstrument())
        return self.listInstrumentTune

    def playBand(self):
        """Hace que la banda toque"""
        self.listInstrumentPlay.clear()
        for i in range(0, len(self.listMariachi)):
            self.listInstrumentPlay.append(self.listMariachi[i].playInstrument())
        return self.listInstrumentPlay

~~~

