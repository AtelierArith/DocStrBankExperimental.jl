```
Val(c)
```

Gibt `Val{c}()` zurück, das keine Laufzeitdaten enthält. Typen wie dieser können verwendet werden, um Informationen zwischen Funktionen durch den Wert `c` zu übergeben, der ein `isbits`-Wert oder ein `Symbol` sein muss. Der Zweck dieser Konstruktion ist es, direkt (zur Compile-Zeit) auf Konstanten zu dispatchen, ohne den Wert der Konstanten zur Laufzeit testen zu müssen.

# Beispiele

```jldoctest
julia> f(::Val{true}) = "Gut"
f (generische Funktion mit 1 Methode)

julia> f(::Val{false}) = "Schlecht"
f (generische Funktion mit 2 Methoden)

julia> f(Val(true))
"Gut"
```
