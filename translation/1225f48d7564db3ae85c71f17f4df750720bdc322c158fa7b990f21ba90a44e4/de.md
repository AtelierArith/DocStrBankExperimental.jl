```
isequal(x)
```

Erstellen Sie eine Funktion, die ihr Argument mit `x` unter Verwendung von [`isequal`](@ref) vergleicht, d.h. eine Funktion, die äquivalent zu `y -> isequal(y, x)` ist.

Die zurückgegebene Funktion ist vom Typ `Base.Fix2{typeof(isequal)}`, die verwendet werden kann, um spezialisierte Methoden zu implementieren.
