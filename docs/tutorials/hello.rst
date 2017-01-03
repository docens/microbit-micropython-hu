Helló, Világ!
-------------

A programozást hagyományosan úgy kezdjük, hogy a számítógéppel kiíratjuk, hogy "Helló, Világ!".

.. image:: ../scroll-hello.gif

Ez MicroPythonnal egyszerű::

    from microbit import *
    display.scroll("Helló, Világ!")

Minden sornak fontos szerepe van. Az első sor::

    from microbit import *

...megmondja a MicroPythonnak, hogy szerezzen meg mindent, ami ahhoz kell, hogy a BBC micro:bittel együtt tudjon működni. Minden ehhez szükséges dolgot egy ``microbit`` nevű modul tartalmaz (a modul egy könyvtár, ami előre megírt kódot tartalmaz). Amikor importálsz (``import``) valamit, akkor megmondod a MicroPythonnak, hogy szeretnéd azt használni. Pythonban a ``*`` jelenti azt, hogy *minden(t)*. Tehát a ``from microbit import *`` sor magyarul azt jelenti, hogy "mindent szeretnék tudni használni, ami a microbit könyvtárban van".

A második sor::

    display.scroll("Helló, Világ!")

...megmondja a MicroPythonnak, hogy a kijelzőn futtassa végig a "Helló, Világ!" *stringet* (a programozásban stringnek nevezik a karakterek sorozatát). A ``display`` a ``microbit`` modul egyik objektuma, ami az eszköz kijelzőjét jelöli. A kijelzőt utasíthatjuk dolgok elvézésére egy ponttal (``.``), amit egy parancsnak kinéző kifejezés követ (ezeket a kifejezéseket *metódusnak* nevezzük). Ebben az esetben a ``scroll`` metódust használjuk. Mivel a ``scroll`` metódusnak tudnia kell, hogy milyen karaktereket szeretnénk végigfuttatni a képernyőn, ezt zárójelek között két idézőjel közé rakjuk. Ezeket *argumentumoknak* nevezzük. Vagyis a ``display.scroll(Helló, Világ!")`` sor magyarul: "a kijelzőn szeretném végigfuttatni a "Helló, Világ!" szöveget". Ha egy metódusnak nincs argumentuma, akkor két üres zárójelet teszünk: ``()``.

Másold be a "Helló, Világ!" kódot a szerkesztődbe és futtasd az eszközön. Ki tudod találni, hogyan kell megváltoztatni az üzenetet? Be tudod állítani, hogy neked köszönjön? Például én úgy írnám át, hogy azt írja ki, hogy "Helló, Dani!". Egy kis segítség: a ``scroll`` metódus argumentumát kell megváltoztatni.

.. warning::

    Lehet, hogy nem fog működni. :-)
    
    Itt válnak a dolgok izgalmassá és a MicroPython segítőkész próbál lenni. Ha hibát talál, egy segítő üzenetet fog megjeleníteni a micro:bit képernyőjén. Ha tudja, megmondja, hogy a kód melyik sorában van a hiba.
    
    A Python azt várja, hogy **PONTOSAN** a helyes kódot írd. Például a ``Microbit``, ``microbit`` és ``microBit`` nem ugyanazt jelenti a Python számára. Ha a MicroPython ``NameError``-t jelez, az valószínűleg azért van, mert valamit pontatlanul írtál. Ez olyan, mint a különbség "Nicholas" és "Nicolas" között. A nevük hasonlít, mégis két különböző emberről van szó.

    Ha a MicroPython ``SyntaxError``-t jelez, akkor valamit olyan módon írtál, amit a MicroPython nem ért meg. Ellenőrizd, hogy nem hagytál-e ki egy speciális karaktert, mint például ``"`` vagy ``:``. Ez olyan. mintha pontot raknál egy mondat közepére. Nehéz megérteni, hogy mit akarsz mondani pontosan.

    Előfordulhat, hogy a microbited nem reagál: nem tudsz új kódot futtatni rajta vagy kódot beírni a szerkesztődbe. Ha ez történik, akkor húzd ki az USB kábelt (és a töltőt is, ha csatlakoztatva van), majd csatlakoztasd a kábelt újra. Lehet, hogy majd ki is kell lépned és újraindítanod a szerkesztőprogramod.
