```
eval(expr)
```

Bewerte einen Ausdruck im globalen Geltungsbereich des enthaltenen Moduls. Jedes `Module` (außer denjenigen, die mit `baremodule` definiert sind) hat seine eigene 1-Argument-Definition von `eval`, die Ausdrücke in diesem Modul bewertet.
