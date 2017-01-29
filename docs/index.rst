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

Projects related to MicroPython on the BBC micro:bit include:

* `Mu <https://github.com/ntoll/mu>`_ - a simple code editor for kids, teachers and beginner programmers. Probably the easiest way for people to program MicroPython on the BBC micro:bit.
* `uFlash <https://uflash.readthedocs.io/en/latest/>`_ - a command line tool for flashing raw Python scripts onto a BBC micro:bit.

.. toctree::
    :maxdepth: 2
    :caption: Tutorials

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
   :caption: API Reference

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
   :caption: Developer Guide

   devguide/installation
   devguide/flashfirmware
   devguide/repl
   devguide/devfaq
   devguide/contributing

.. toctree::
   :maxdepth: 2
   :caption: Indices and tables

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`
