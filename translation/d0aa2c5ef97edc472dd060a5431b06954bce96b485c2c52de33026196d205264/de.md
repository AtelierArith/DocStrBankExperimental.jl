```
>(x)
```

Erstellen Sie eine Funktion, die ihr Argument mit `x` unter Verwendung von [`>`](@ref) vergleicht, d.h. eine Funktion, die äquivalent zu `y -> y > x` ist. Die zurückgegebene Funktion hat den Typ `Base.Fix2{typeof(>)}`, der verwendet werden kann, um spezialisierte Methoden zu implementieren.

!!! compat "Julia 1.2"
    Diese Funktionalität erfordert mindestens Julia 1.2.

