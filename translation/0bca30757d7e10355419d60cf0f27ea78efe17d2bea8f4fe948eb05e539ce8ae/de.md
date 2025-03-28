```
unsafe_copyto!(dest::Ptr{T}, src::Ptr{T}, N)
```

Kopiere `N` Elemente von einem Quellzeiger zu einem Ziel, ohne Überprüfung. Die Größe eines Elements wird durch den Typ der Zeiger bestimmt.

Das `unsafe` Präfix dieser Funktion zeigt an, dass keine Validierung der Zeiger `dest` und `src` durchgeführt wird, um sicherzustellen, dass sie gültig sind. Falsche Verwendung kann dein Programm beschädigen oder einen Segfault verursachen, ähnlich wie in C.
