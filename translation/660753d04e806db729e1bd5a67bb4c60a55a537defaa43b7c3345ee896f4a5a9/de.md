```
issetequal(x)
```

Erstellen Sie eine Funktion, die ihr Argument mit `x` unter Verwendung von [`issetequal`](@ref) vergleicht, d.h. eine Funktion, die äquivalent zu `y -> issetequal(y, x)` ist. Die zurückgegebene Funktion ist vom Typ `Base.Fix2{typeof(issetequal)}`, die verwendet werden kann, um spezialisierte Methoden zu implementieren.

!!! compat "Julia 1.11"
    Diese Funktionalität erfordert mindestens Julia 1.11.

