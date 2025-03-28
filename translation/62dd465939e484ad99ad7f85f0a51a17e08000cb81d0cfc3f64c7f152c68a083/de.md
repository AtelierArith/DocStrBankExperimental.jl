```
unsafe_copyto!(dest::Array, do, src::Array, so, N)
```

Kopiere `N` Elemente von einem Quellarray zu einem Zielarray, beginnend am linearen Index `so` im Quellarray und `do` im Zielarray (1-indiziert).

Das `unsafe` Präfix dieser Funktion zeigt an, dass keine Validierung durchgeführt wird, um sicherzustellen, dass N in beiden Arrays im zulässigen Bereich liegt. Falsche Verwendung kann dein Programm beschädigen oder einen Segfault verursachen, ähnlich wie in C.
