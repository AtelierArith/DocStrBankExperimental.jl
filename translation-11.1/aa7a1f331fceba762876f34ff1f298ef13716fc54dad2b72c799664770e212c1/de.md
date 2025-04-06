```
abstract type
```

`abstract type` deklariert einen Typ, der nicht instanziiert werden kann, und dient nur als Knoten im Typgraphen, wodurch Mengen verwandter konkreter Typen beschrieben werden: jene konkreten Typen, die ihre Nachkommen sind. Abstrakte Typen bilden die konzeptionelle Hierarchie, die Julias Typsystem mehr als nur eine Sammlung von Objektimplementierungen macht. Zum Beispiel:

```julia
abstract type Number end
abstract type Real <: Number end
```

[`Number`](@ref) hat keinen Supertyp, während [`Real`](@ref) ein abstrakter Subtyp von `Number` ist.
