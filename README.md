# Wat doet het?
Bedoeling was om kivy te laten werken in een webbrowser d.m.v. pyodide. 

cf. de readme in de pyodide map voor extra info


# cpython errors

Raadpleeg https://github.com/bansdude/cpython/blob/master/build/3.7.4/Python-3.7.4/config.log

Errors waar volgende keywords in voorkomen, komen ook voor bij het builden van kivy met pyodide:

`/src/emsdk/emsdk/emscripten/tag-1.38.30/src/library_pthread_stub.js`

## Errors fixen
Zie bovenstaande link


# Zelf proberen builden?
Dit project neemt ongeveer 8 GB aan ruimte in beslag. 

### optie 1

## Benodigdheden voor elke build
1. Download de masterbranch van pyodide

    https://github.com/iodide-project/pyodide#using-docker


2. Download de kivy fork 

    https://github.com/Epse/kivy/tree/emscripten-wip

### optie 2

1.  Download deze repository en volg een van onderstaande stappenplannen.

---
## Starten van scratch met bron code

### Stappenplan deel 1

Volg de instructies op in de readme van pyodide zelf. (https://pyodide.readthedocs.io/en/latest/building_from_sources.html)

### Stappenplan deel 2

1. Installeer cython met volgend commando `pip install cython`

2. Zet nu de kivy map in de pyodide map.

3. Pas in de file `Kivy/em/makefile` de regel 
`PYODIDE_ROOT=` aan naar de locatie waar pyodide gebuild is.

4. Start dan het commando `make` in de map `Kivy/em`.


---
## Starten van scratch met docker

### benodigdheden
1. Zorg ervoor dat je docker hebt staan.


### Stappenplan

1. Installeer cython met volgend commando 
`pip install cython`

2. Zet de Kivy map in de pyodide map.

3. Pas in de file `Kivy/em/makefile` volgende regel aan
`PYODIDE_ROOT=/src`.

4. Start docker op en start het commando `./run_docker` in de pyodide map.

5. Type het commando `make` nadat docker is opgestart.

6. Installeer vervolgens cython met het commando `pip install cython`.

7. Start dan het commando `make` in `kivy/em`.
