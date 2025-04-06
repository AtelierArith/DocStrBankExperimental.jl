```
clear!(syms, pids=workers(); mod=Main)
```

Löscht globale Bindungen in Modulen, indem sie auf `nothing` initialisiert werden. `syms` sollte vom Typ [`Symbol`](@ref) oder einer Sammlung von `Symbol`s sein. `pids` und `mod` identifizieren die Prozesse und das Modul, in dem globale Variablen neu initialisiert werden sollen. Nur die Namen, die unter `mod` definiert sind, werden gelöscht.

Eine Ausnahme wird ausgelöst, wenn ein globaler Konstante angefordert wird, gelöscht zu werden.
