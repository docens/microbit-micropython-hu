Bevezető
------------

Azt ajánljuk, hogy töltsd le és használd a `Mu szerkesztőt <http://codewith.mu/>`_ amíg ezeket a leckéket tanulmányozod. A Mu letöltéséről és installációjáról további információt a honlapján találsz. Esetleg installálnod fog kelleni egy meghajtót, ez a platformodtól függ (minden instrukciót megtalálsz a honlapon).

A Mu Windowszal, OSX-szel és Linuxszal is kompatibilis.

Miután installáltad a Mut, egy USB kábellel kösd össze a micro:bitedet a számítógépeddel.

Írd be a kódodat a szerkesztőablakba, majd nyomj rá a "Flash" gombra, hogy az lefusson a micro:biten. Ha nem működik, ellenőrizd le, hogy a micro:bit megjelenik-e USB tárolóeszközként a fájlkezelődben.

.. toctree::
    :maxdepth: 2
    :caption: Leckék

    hello
    images
    buttons
    io
    music
    random
    movement
    gestures
    direction
    storage
    speech
    network
    radio
    next

A Python `a világ egyik legnépszerűbb <http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html>`_ programozási nyelve. Valószínűleg minden nap (anélkül, hogy tudnál róla) használsz Python nyelvet használó programokat. Rengeteg különböző cég és szervezet használ Pythont nagyon sokféle applikációhoz. Google, Nasa, Bank of America, Disney, CERN, YouTube, Mozilla, The Guardian - a lista ennél sokkal hosszabb, a Pythont használó cégek lefedik a gazdaság, tudomány és művészet különböző területeit.

Például emlékszel `a gravitációs hullámok felfedezésére <http://www.bbc.co.uk/news/science-environment-35552207>`_? Az eszköz, ami a méréseket végezte, `Python nyelvet használt <https://www.reddit.com/r/IAmA/comments/45g8qu/we_are_the_ligo_scientific_collaboration_and_we/czxnlux>`_.

Röviden, ha Pythont tanulsz vagy tanítasz, azzal egy olyan készséget fejlesztesz, aminek hasznát veheted az emberi törekvések minden területén.

Az egyik ilyen terület a BBC lenyűgöző micro:bit eszköze. Ezen a Python MicroPython nevű verziója fut, ami kisméretű eszközökhöz lett kitalálva, mint amilyen a BBC micro:bit. A MicroPython a Python 3 teljes implementációja, vagyis amikor más dolgokat fogsz programozni (például a Raspberry Pit, Python nyelven), akkor is ugyanezt a nyelvet fogod használni.

A MicroPython nem tartalmaz minden programkönyvtárat, ami a "normális" Pythonnal jár. Viszont írtunk a MicroPythonhoz egy különleges ``microbit`` modult, aminek segítségével lehet kezelni az eszközt.

A Python és a MicroPython szoftverek ingyenesek. Ez nem csak azt jelenti, hogy nem kell a használatukért fizetni, de Te is segíthetsz a Python közösségnek. Ennek a formája lehet egy kód, dokumentáció, hibajelentés, egy közösségi csoport létrehozása, vagy akár oktatóanyagok írása (mint ez itt). Valójában a Python azon elemei, amik a BBC micro:bithez íródtak, egy nemzetközi, önkéntesekből álló csapat munkája, akik a szabadidejükben dolgoztak.

A dokumentációban található leckék können követhető lépésekben, alapos magyarázatokkal mutatják be a MicroPythont és a BBC micro:bitet. Nyugodtan használd őket iskolai tanórák keretében, vagy csak otthoni tanulásra.

Akkor fogod a legtöbb sikert elérni, ha felfedezel, kísrletezgetsz és játszol. Egy hibás kóddal nem tudod elrondtani az eszközt! Ugorj fejest a programozásba!

Egy kis figyelmeztetés: *sokszor fogsz hibázni*, és ez rendben is van. **A jó szoftverfejlesztők a hibákból tanulnak**. Akik közülünk szoftverfejlesztőként dolgoznak, élvezetesnek találják a hibakeresést és a hibák megismétlésének elkerülését.

Ha kétségek gyötörnének, csak idézd fel a MicroPython alapelvét::
    
    Kódolj,
    Hackeld meg,
    A kevesebb több,
    Ne bonyolítsd túl,
    A kicsi gyönyörű,
    
    Légy bátor! Merj hibázni! Tanulj, és érezd jól magad!
    Fejezd ki magad a MicroPythonnal.
    
    Jó hackelést! :-)

Sok szerencsét!
