```
__precompile__(isprecompilable::Bool)
```

Geben Sie an, ob die Datei, die diese Funktion aufruft, vorcompilierbar ist, standardmäßig `true`. Wenn ein Modul oder eine Datei *nicht* sicher vorcompilierbar ist, sollte es `__precompile__(false)` aufrufen, um einen Fehler auszulösen, wenn Julia versucht, es vorzukompilieren.
