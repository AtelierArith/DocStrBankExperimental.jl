```
isdisjoint(x)
```

Erstellen Sie eine Funktion, die ihr Argument mit `x` unter Verwendung von [`isdisjoint`](@ref) vergleicht, d.h. eine Funktion, die äquivalent zu `y -> isdisjoint(y, x)` ist. Die zurückgegebene Funktion ist vom Typ `Base.Fix2{typeof(isdisjoint)}`, die verwendet werden kann, um spezialisierte Methoden zu implementieren.

!!! compat "Julia 1.11"
    Diese Funktionalität erfordert mindestens Julia 1.11.

