Bemenet/Kimenet
------------

A BBC mirco:bit alsó szegélye mentén találhatóak fém sávok, amiktől úgy néz ki, mintha fogai lennének. Ezek a bemeneti/kimeneti lábak (angolul input/output pins, röviden I/O pins).

.. image:: blue-microbit.png

Néhány láb nagyobb, mint a többi, így lehet krokodilcsipeszt hozzájuk csatlakoztatni. Ezek azok, amik 0, 1, 2, 3V és GND címkével vannak ellátva (a számítógépek mindig 0-tól kezdik a számolást). Ha hozzácsatlakoztatsz egy *edge connectort* a készülékhez, be lehet dugni vezetékeket, amik a többi (kisebb) lábhoz csatlakoznak.

Minden egyes lábat a BBC micro:biten egy *objektum* jelöl, aminek a neve ``pinN``, ahol ``N`` a láb (*pin*) száma. Tehát például ha a 0-val jelölt lábbal szeretnél valamit kezdeni, akkor használd a ``pin0`` nevű objektumot.

Egyszerű!

Ezekhez az objektumokhoz különféle *metódusok* tartoznak, attól függően, hogy az adott láb mit tud csinálni.

Csikis Python
+++++++++++++++

A legegyszerűbb példa a lábak általi bemenetre az, ha megnézzük, hogy meg vannak-e érintve (angolul *is touched*). Meg tudod csikizni az eszközödet, hogy az nevessen::

    from microbit import *

    while True:
        if pin0.is_touched():
            display.show(Image.HAPPY)
        else:
            display.show(Image.SAD)

Az egyik kezeddel fogd meg az esközt a GND lábnál. Aztán a másik kezeddel érintsd meg (vagy csikizd meg) a 0-s lábat. Láthatod a képernyőn, ahogy a szomorú fej boldoggá válik!

Ez a bemenet vizsgálatának egyik legalapvetőbb módja. Az igazi mók akkor kezdődik, ha áramköröket és egyéb eszközöket csatlakoztatsz az eszközhöz a labako keresztül.

Bleeps and Bloops
+++++++++++++++++

The simplest thing we can attach to the device is a Piezo buzzer. We're going
to use it for output.

.. image:: piezo_buzzer.jpg

These small devices play a high-pitched bleep when connected to a circuit. To
attach one to your BBC micro:bit you should attach crocodile clips to pin 0 and
GND (as shown below).

.. image:: pin0-gnd.png

The wire from pin 0 should be attached to the positive connector on the buzzer
and the wire from GND to the negative connector.

The following program will cause the buzzer to make a sound::

    from microbit import *

    pin0.write_digital(1)

This is fun for about 5 seconds and then you'll want to make the horrible
squeaking stop. Let's improve our example and make the device bleep::

    from microbit import *

    while True:
        pin0.write_digital(1)
        sleep(20)
        pin0.write_digital(0)
        sleep(480)

Can you work out how this script works? Remember that ``1`` is "on" and ``0``
is "off" in the digital world.

The device is put into an infinite loop and immediately switches pin 0 on. This
causes the buzzer to emit a beep. While the buzzer is beeping, the device
sleeps for twenty milliseconds and then switches pin 0 off. This gives the
effect of a short bleep. Finally, the device sleeps for 480 milliseconds before
looping back and starting all over again. This means you'll get two bleeps per
second (one every 500 milliseconds).

We've made a very simple metronome!

.. footer:: The image of the pizeo buzzer is CC BY-NC-SA 3.0 from https://www.flickr.com/photos/tronixstuff/4821350094
