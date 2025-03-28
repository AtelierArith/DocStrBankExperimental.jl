```
find_library(names [, locations])
```

Durchsucht die erste Bibliothek in `names` in den Pfaden der `locations`-Liste, `DL_LOAD_PATH` oder Systembibliothekspfaden (in dieser Reihenfolge), die erfolgreich mit dlopen'd werden kann. Bei Erfolg ist der Rückgabewert einer der Namen (möglicherweise mit einem der Pfade in locations vorangestellt). Dieser String kann einer `global const` zugewiesen und als Bibliotheksname in zukünftigen `ccall`-Aufrufen verwendet werden. Bei Misserfolg wird der leere String zurückgegeben.
