```
@generated f
```

`@generated` wird verwendet, um eine Funktion zu kennzeichnen, die generiert wird. Im Körper der generierten Funktion können nur die Typen der Argumente gelesen werden (nicht die Werte). Die Funktion gibt einen zitierten Ausdruck zurück, der ausgewertet wird, wenn die Funktion aufgerufen wird. Das `@generated`-Makro sollte nicht auf Funktionen angewendet werden, die den globalen Bereich verändern oder von veränderlichen Elementen abhängen.

Siehe [Metaprogramming](@ref) für weitere Details.

# Beispiele

```jldoctest
julia> @generated function bar(x)
           if x <: Integer
               return :(x ^ 2)
           else
               return :(x)
           end
       end
bar (generische Funktion mit 1 Methode)

julia> bar(4)
16

julia> bar("baz")
"baz"
```
