# **PATRONES DE DISEÑO**

## Sections

- [Patrones Creacionales](#PATRONES-CREACIONALES)

    -*[1. Abstract Factory](#1.-Abstract-Factory)*

    -*[1.1 Estuctura](#1.1-Estructura)*

    -*[1.2 Código](#1.2-Código)*





## **PATRONES CREACIONALES** 

<div style="text-align: center">

##  **1. Abstract Factory**

> "Abstract Factory es un patrón de diseño que permite crear familias de objetos relacionados sin especificar sus clases concretas".

___

##  **1.1 Estructura**

![Abstract Factory UML](UMLPatterns/AbstractFactory.jpg )


## **1.2 Código**
</div>


~~~python

class Product():
    def chassis(self):
        pass

    def camera(self):
        pass

    def propeller(self):
        pass
~~~
___

~~~python
from Product import Product
from ChassisDJI import ChassisDJI
from PropellerDJI import PropellerDJI
from CameraDJI import CameraDJI


class DJI(Product):

    def chassis(self):
        super().chassis()
        c = ChassisDJI()
        return c.createChassis()

    def camera(self):
        super().camera()
        c = CameraDJI()
        return c.createCamera()

    def propeller(self):
        super().propeller()
        p = PropellerDJI()
        return p.createPropeller()

~~~

___

~~~python

from Product import Product
from ChassisHubsand import ChassisHubsand
from PropellerHubsand import PropellerHubsand
from CameraHubsand import CameraHubsand


class Hubsand (Product):
    def chassis(self):
        super().chassis()
        h = ChassisHubsand()
        return h.createChassis()

    def camera(self):
        super().camera()
        h = CameraHubsand()
        return h.createCamera()

    def propeller(self):
        super().propeller()
        h = PropellerHubsand()
        return h.createPropeller()

~~~

___

~~~python
class Camera():

    def createCamera(self):
        pass
~~~
___

~~~python
from Camera import Camera


class CameraDJI(Camera):
    def createCamera(self):
        super().createCamera()
        return "Camara de DJI"

~~~
___

~~~python
from Camera import Camera


class CameraHubsand(Camera):

    def createCamera(self):
        super().createCamera()
        return "Cámara de Hubsand"


~~~
___

~~~python
class Chassis():
    def createChassis(self):
        pass

~~~
___

~~~python
from Chassis import Chassis


class ChassisDJI(Chassis):
    def createChassis(self):
        super().createChassis()
        return "Chasis de DJI"

~~~
___

~~~python
from Chassis import Chassis


class ChassisHubsand(Chassis):
    def createChassis(self):
        super().createChassis()
        return "chasis de hubsand"

~~~
___

~~~python
class Propeller():
    def createPropeller(self):
        pass

~~~
___

~~~python
from Propeller import Propeller


class PropellerDJI(Propeller):
    def createPropeller(self):
        super().createPropeller()
        return "Helices de DJI"

~~~
___

~~~python
from Propeller import Propeller


class PropellerHubsand(Propeller):
    def createPropeller(self):
        super().createPropeller()
        return "Helices de Hubsand"

~~~
___

~~~python
from DJI import *
from Hubsand import *


class Client():

    def __init__(self):
        self.droneList = [DJI(), Hubsand()]

    def chooseDrone(self):
        drone = int(
            input("¿Qué marca de drone desea?\nMarque 1 para DJI\nMarque 2 para Hubsand\n"))
        if drone == 1:
            brandDrone = self.droneList[0]
        elif drone == 2:
            brandDrone = self.droneList[1]

        camera = brandDrone.camera()
        chassis = brandDrone.chassis()
        propeller = brandDrone.propeller()

        return f"se ha creado {camera}, {chassis}, {propeller}"


~~~
___

~~~python
from Client import Client

c = Client()
print(c.chooseDrone())


~~~
