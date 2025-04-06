```
f ∘ g
```

Funktionen zusammensetzen: d.h. `(f ∘ g)(args...; kwargs...)` bedeutet `f(g(args...; kwargs...))`. Das Symbol `∘` kann im Julia REPL (und in den meisten entsprechend konfigurierten Editoren) eingegeben werden, indem man `\circ<tab>` tippt.

Die Funktionskomposition funktioniert auch in Präfixform: `∘(f, g)` ist dasselbe wie `f ∘ g`. Die Präfixform unterstützt die Komposition mehrerer Funktionen: `∘(f, g, h) = f ∘ g ∘ h` und das Splatting `∘(fs...)` zur Komposition einer iterierbaren Sammlung von Funktionen. Das letzte Argument von `∘` wird zuerst ausgeführt.

!!! compat "Julia 1.4"
    Die Komposition mehrerer Funktionen erfordert mindestens Julia 1.4.


!!! compat "Julia 1.5"
    Die Komposition einer Funktion ∘(f) erfordert mindestens Julia 1.5.


!!! compat "Julia 1.7"
    Die Verwendung von Schlüsselwortargumenten erfordert mindestens Julia 1.7.


# Beispiele

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (Kategorie Lu: Buchstabe, Großbuchstabe)
 'B': ASCII/Unicode U+0042 (Kategorie Lu: Buchstabe, Großbuchstabe)
 'C': ASCII/Unicode U+0043 (Kategorie Lu: Buchstabe, Großbuchstabe)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

Siehe auch [`ComposedFunction`](@ref), [`!f::Function`](@ref).
