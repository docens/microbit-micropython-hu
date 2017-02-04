.. BBC Microbit Micropython documentation master file, created by
   sphinx-quickstart on Tue Oct 20 10:41:30 2015.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

BBC micro:bit MicroPython dokumentáció
=======================================

Köszöntünk!

A BBC micro:bit egy kicsi számítástechnikai eszköz, elsősorban gyerekeknek. A micro:bit többek között a népszerű Python programozási nyelvet is érti. A MicroPython a Python nyelv azon verziója, ami fut a BBC micro:biten.

Ez a dokumentáció leckéket tartalmaz tanároknak és API dokumentációt fejlesztőknek (vess egy pillantást a balra lévő tárgymutatóra). Reméljük, szívesen segítesz a BBC micro:bit fejlesztésében.

Ha a programozás új neked, tanár vagy, vagy csak nem tudod, mi legyen az első lépés, kezdd az oktatóanyaggal.

.. image:: comic.png

Ha a közösség tagja szeretnél lenni, iratkozz fel a microbit@python.org levelezőlistára (https://mail.python.org/mailman/listinfo/microbit).

.. note::
    
    Ez a projekt fejlesztés alatt áll.
    
..  This project is under active development. Please help other
    developers by adding tips, how-tos, and Q&A to this document.
    Thanks!

Néhány MicroPythonhoz és a BBC micro:bithez kapcsolódó projekt:

* `Mu <https://github.com/ntoll/mu>`_ - egy egyszerű kódszerkesztő gyerekeknek, tanároknak és kezdő rogramozóknak. Az egyik legegyszerűbb módja a BBC micro:bit MicroPython nyelven való programozásának.
* `uFlash <https://uflash.readthedocs.io/en/latest/>`_ - egy parancssori eszköz, amivel PYthon kódot tudsz lefuttatni a BBC micro:biteden.

.. toctree::
    :maxdepth: 2
    :caption: Leckék

    tutorials/introduction
    tutorials/hello
    tutorials/images
    tutorials/buttons
    tutorials/io
    tutorials/music
    tutorials/random
    tutorials/movement
    tutorials/gestures
    tutorials/direction
    tutorials/storage
    tutorials/speech
    tutorials/network
    tutorials/radio
    tutorials/next

.. toctree::
   :maxdepth: 2
   :caption: API referencia

   microbit_micropython_api.rst
   microbit.rst
   accelerometer.rst
   ble.rst
   button.rst
   compass.rst
   display.rst
   filesystem.rst
   i2c.rst
   image.rst
   music.rst
   neopixel.rst
   os.rst
   pin.rst
   radio.rst
   random.rst
   speech.rst
   spi.rst
   uart.rst

.. toctree::
   :maxdepth: 2
   :caption: Fejlesztői útmutató

   devguide/installation
   devguide/flashfirmware
   devguide/repl
   devguide/devfaq
   devguide/contributing

.. toctree::
   :maxdepth: 2
   :caption: Indexek és táblázatok

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
