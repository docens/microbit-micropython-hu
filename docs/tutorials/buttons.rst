Gombok
-------

Eddig olyan kódokat írtunk, amik megcsináltattak valamit az eszközzel. Ezt *kimenetnek* nevezzük. Viszont arra is szükségünk van, hogy az eszközünk tudjon reagálni is a dolgokra. Ezeket a dolgokat *bemenetnek* hívjuk.

Könnyű megjegyezni: a kimenet az, amit az eszköz kijelez, kiír, míg a bemenet az, amit beküldünk neki feldolgozásra.

A micro:bit legszembetűnőbb beviteli eszköze a két (``A`` és ``B`` jelölésű) gomb. Valahogy meg kell oldanunk, hogy a MicroPython reagáljon a gombnyomásokra.

Ez kifejezetten egyszerű::

    from microbit import *

    sleep(10000)
    display.scroll(str(button_a.get_presses()))

Ez a kód mindössze annyit csinál, hogy tízezer milliszekundum (10 mp) *alvás* (vagyis késleltetés) után végigfuttatja a képernyőn azt a számot, ahányszor megnyomtad az ``A`` gombot. Ennyi!

Igaz, hogy ez egy elég felesleges program, viszont megjelenik benne néhány érdekes, új koncepció:

#. A ``sleep`` (magyarul alvás) *függvény* elaltatja, azaz késlelteti a következő kódrész lefutását valahány milliszekundummal. Ha tehát szünetet szeretnél tenni a programodba, azt így tudod megtenni. Egy *függvény* pont olyan, mint egy *metódus*, csak nem kapcsoljuk *objektumhoz* egy pont segítségével.
#. Van egy ``button_a`` nevű objektum, és a ``get_presses`` *metódus* segítségével megkaphatjuk, hogy hányszor lett megnyomva.

Mivel a ``get_presses`` metódus egy numerikus értéket ad vissza és a ``display.scroll`` metódus csak karaktereket tud mutatni, át kell alakítanunk a numerikus értéket egy sztringgé. Ezt a ``str`` függvénnyel tudjuk megtenni, ami dolgokat sztringekké alakít át.

A harmadik sor egy kicsit olyan, mint egy hagyma. A zárójelek a hagyma héjai. Észreveheted, hogy a ``button_a.get_presses`` benne van a ``str`` függvényben, ami meg a ``display.scroll``-ban van benne. A Python először a legbelső kódrészletet futtatja le, majd egyre kijjebb halad. Ezt *egymásba ágyazásnak* hívjuk - az orosz matrjoska babák programozásban használt megfelelője. 

.. image:: matrioshka.jpg

Tegyük fel, hogy megnyomtad a gombot 10-szer. Nézzük meg, hogy jön rá a Python, hogy mit csinál a harmadik sor:

A Python látja az egész sort, majd megállapítja a ``get_presses`` metódus értékét::

    display.scroll(str(button_a.get_presses()))

Most, hogy tudja, hogy hány gombnyomás történt, átalakítja a numerikus értéket sztringgé::

    display.scroll(str(10))

Végül, a kapott sztringet végigfuttatja a képernyőn::

    display.scroll("10")
    
Ez sok melónak tűnik, mégis a MicroPython elképesztő gyorsan futtatja le ezt a kódot.

While ciklusok
+++++++++++

Gyakran szükséges, hogy a kód ne azonnal fusson le, hanem várjon egy esemény bekövetkezéséig. Ehhez az kell, hogy a program ismételjen egy kódrészletet, ami megmondja, hogy hogyan reagáljon konkrét eseményekre (mint például egy gomb megnyomására).

A Pythonban ciklusokhoz a ``while`` (magyarul míg) kulcsszót használjuk. Ez leellenőrzi, hogy valami igaz-e (``True``). Ha igen, akkor lefutatt egy *kódtömböt*, amit angolul a ciklus *body*-jának (magyarul test) hívnak. Ha nem igaz a feltétel, akkor a program kitör a ciklusból, nem futtatja le a bodyban lévő kódot, hanem továbbhalad a kódban. 

A Pythonban egyszerű kódtömböt definiálni. Mondjuk, hogy írtam egy tennivaló listát egy papírra. Valahogy így fog kinézni::

    Vásárlás
    Megjavítani a törött ereszt
    Fűnyírás

Ha a pontokat jobban ki szeretném fejteni, akkor valami ilyesmit írnék::

    Vásárlás:
        Tojás
        Bacon
        Paradicsom
    Megjavítani a törött ereszt:
        Létrát kölcsönkérni a szomszédtól
        Kalapácsot és szögeket keresni
        Létrát visszavinni
    Fűnyírás:
        Tó körül körülnézni, hátha vannak békák
        Leelenőrizni a fűnyíró üzemanyagszintjét

A főfeladatokat több kisebbb feladatra bontottuk szét. Minden kisebb feladat a hozzá tartozó főfeladat alá kerül behúzással. Vagyis a ``Tojás``, a ``Bacon`` és a ``Paradicsom`` a ``Vásárlás``-hoz kapcsolódik. A behúzás miatt első ránézésre meg lehet állapítani, hogy hogyan viszonyulnak egymáshoz a feladatok.

Ezt hívjuk *egymásba ágyazásnak*. Egymásba ágyazással definiáljuk a kódtömböket::

    from microbit import *

    while running_time() < 10000:
        display.show(Image.ASLEEP)

    display.show(Image.SURPRISED)

A ``running_time`` (magyarul futás ideje) függvény azt a számot adja vissza, ahány milliszekundum eltelt a készülék beindítása óta.

A ``while running_time() < 10000:`` sor megnézi, hogy a program futásának ideje kevesebb-e, mint 10000 milliszekundum (10 mp). Ha igen, akkor a kijelző megjeleníti az ``Image.ASLEEP`` képet. Figyeld meg, hogy a harmadik sor be van húzva a ``while`` feltétel alatt, *pont mint a tennivaló listánkban*. 

Mikor a futás ideje nagyobb vagy egyenlő mint 10000 milliszekundum, a képernyő az ``Image.SURPRISED`` képet fogja mutatni. Hogy miért? Mert a ``while`` feltétel már hamis (``False``) lesz, a ``running_time`` már nem lesz ``< 10000``. Ebben az esetben a ciklusnak vége van, a program továbblép a ``while`` ciklus kódtömbjén. Az eszköz úgy fog kinézni, mintha 10 másodpercet aludna, majd csodálkozó fejjel felébredne.

Próbáld ki!

Események kezelése
+++++++++++++++++

Ha azt szeretnénk, hogy a MicroPython reagáljon a gombok megnyomására, akkor egy végtelen ciklust kell létrehoznunk, ami ellenőrzi, hogy a gomb meg lett-e nyomva (``is_pressed``).

Végtelen ciklusokat könnyen csinálhatunk::

    while True:
        # Csinálj dolgokat

(A ``while`` ciklus ellenőrzi, hogy egy feltétel igaz-e, és ez alapján dönti el, hogy lefutassa-e a kódtömbjét. Mivel a ``True`` (igaz) egyértelműen mindig igaz lesz, ezért végtelen ciklust kapunk!)

Csináljunk egy nagyon egyszerű, virtuális állatot! Mindig szomorú lesz, kivéve, ha megnyomod az ``A`` gombot. Ha megnyomod a ``B`` gombot, meghal. (Ez nem egy túl barátságos játék, de esetleg gondolkozhatsz rajta, hogy hogyan tegyük azzá.)::

    from microbit import *

    while True:
        if button_a.is_pressed():
            display.show(Image.HAPPY)
        elif button_b.is_pressed():
            break
        else:
            display.show(Image.SAD)

    display.clear()

Látod hogyan ellenőrizzük, hogy melyik gombokat nyomják meg éppen? Ehhez az ``if`` (magyarul ha), az ``elif`` (else if rövidítése - másik ha) és az ``else`` (más) kulcsszavakat használjuk. Ezeket *feltételeknek* hívjuk. Itt látható a működésük::

    if valami igaz (True):
        # csinálj valamit
    elif valami más dolog igaz (True):
        # csinálj valami mást
    else:
        # itt is csinálj valamit

Az ``is_pressed`` (magyarul meg van-e nyomva) metódus csak kétféle választ adhat: ``True`` vagy ``False`` (igaz vagy hamis). Ha épp nyomod a gombot, akkor ``True``-t fog visszaadni, egyébként ``False``-ot. A fenti kód magyarra fordítva: "amikor megnyomják az A gombot, akkor mutass egy vidám arcot, ha nem nyomják meg, viszont a B gombot igen, akkor lépj ki a ciklusból, egyébként meg mutass egy szomorú arcot". A ``break`` utasítással kilépünk a ciklusból (ezután már nem fog ismétlődni tovább a ciklus).

A legvégén, amikor a virtuális állatunk meghalt, a ``clear`` metódussal eltüntetünk mindent a képernyőről.

Át tudod írni úgy a kódot, hogy a játék kevésbé legyen tragikus? Hogyan ellenőriznéd le, hogy *mindkét* gomb meg van-e nyomva? (Segítség: a Pythonban az ``and`` (és), az ``or`` (vagy) és a ``not`` (nem) logikai operátorok segítségével leelenőrizhetünk több feltételt is.)

.. footer:: A matrjoska babáról készült fotó licensze: CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=69402
