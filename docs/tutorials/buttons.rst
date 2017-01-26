Gombok
-------

Eddig olyan kódokat írtunk, amik véghez vitettek valamit az eszközzel. Ezt *kimenetnek* nevezzük. Viszont arra is szükségünk van, hogy az eszközünk tudjon reagálni is a dolgokra. Ezeket a dolgokat *bemenetnek* hívjuk.

Könnyű megjegyezni: a kimenet az, amit az eszköz kijelez, kiír, míg a bemenet az, amit beküldünk neki feldolgozásra.

A micro:bit legszembetűnőbb beviteli eszközei a két (``A`` és ``B`` jelölésű) gomb. Valahogy meg kell oldanunk, hogy a MicroPython reagáljon a gombnyomásokra.

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

Event Loops
+++++++++++

Often you need your program to hang around waiting for something to happen. To
do this you make it loop around a piece of code that defines how to react to
certain expected events such as a button press.

To make loops in Python you use the ``while`` keyword. It checks if something
is ``True``. If it is, it runs a *block of code* called the *body* of the loop.
If it isn't, it breaks out of the loop (ignoring the body) and the rest of the
program can continue.

Python makes it easy to define blocks of code. Say I have a to-do list written
on a piece of paper. It probably looks something like this::

    Shopping
    Fix broken gutter
    Mow the lawn

If I wanted to break down my to-do list a bit further, I might write something
like this::

    Shopping:
        Eggs
        Bacon
        Tomatoes
    Fix broken gutter:
        Borrow ladder from next door
        Find hammer and nails
        Return ladder
    Mow the lawn:
        Check lawn around pond for frogs
        Check mower fuel level

It's obvious that the main tasks are broken down into sub-tasks that are
*indented* underneath the main task to which they are related. So ``Eggs``,
``Bacon`` and ``Tomatoes`` are obviously related to ``Shopping``. By indenting
things we make it easy to see, at a glance, how the tasks relate to each other.

This is called *nesting*. We use nesting to define blocks of code like this::

    from microbit import *

    while running_time() < 10000:
        display.show(Image.ASLEEP)

    display.show(Image.SURPRISED)

The ``running_time`` function returns the number of milliseconds since the
device started.

The ``while running_time() < 10000:`` line checks if the running time is less
than 10000 milliseconds (i.e. 10 seconds). If it is, *and this is where we can
see scoping in action*, then it'll display ``Image.ASLEEP``. Notice how this is
indented underneath the ``while`` statement *just like in our to-do list*.

Obviously, if the running time is equal to or greater than 10000 milliseconds
then the display will show ``Image.SURPRISED``. Why? Because the ``while``
condition will be False (``running_time`` is no longer ``< 10000``). In that
case the loop is finished and the program will continue after the ``while``
loop's block of code. It'll look like your device is asleep for 10
seconds before waking up with a surprised look on its face.

Try it!

Handling an Event
+++++++++++++++++

If we want MicroPython to react to button press events we should put it into
an infinite loop and check if the button ``is_pressed``.

An infinite loop is easy::

    while True:
        # Do stuff

(Remember, ``while`` checks if something is ``True`` to work out if it should
run its block of code. Since ``True`` is obviously ``True`` for all time, you
get an infinite loop!)

Let's make a very simple cyber-pet. It's always sad unless you're pressing
button ``A``. If you press button ``B`` it dies. (I realise this isn't a very
pleasant game, so perhaps you can figure out how to improve it.)::

    from microbit import *

    while True:
        if button_a.is_pressed():
            display.show(Image.HAPPY)
        elif button_b.is_pressed():
            break
        else:
            display.show(Image.SAD)

    display.clear()

Can you see how we check what buttons are pressed? We used ``if``,
``elif`` (short for "else if") and ``else``. These are called *conditionals*
and work like this::

    if something is True:
        # do one thing
    elif some other thing is True:
        # do another thing
    else:
        # do yet another thing.

This is remarkably similar to English!

The ``is_pressed`` method only produces two results: ``True`` or ``False``.
If you're pressing the button it returns ``True``, otherwise it returns
``False``. The code above is saying, in English, "for ever and ever, if
button A is pressed then show a happy face, else if button B is pressed break
out of the loop, otherwise display a sad face." We break out of the loop (stop
the program running for ever and ever) with the ``break`` statement.

At the very end, when the cyber-pet is dead, we ``clear`` the display.

Can you think of ways to make this game less tragic? How would you check if
*both* buttons are pressed? (Hint: Python has ``and``, ``or`` and ``not``
logical operators to help check multiple truth statements (things that
produce either ``True`` or ``False`` results).

.. footer:: A matrjoska babáról készült fotó licensze: CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=69402
