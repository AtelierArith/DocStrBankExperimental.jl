```
eachsplit(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
eachsplit(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Teile `str` an den Vorkommen des Trennzeichens `dlm` und gebe einen Iterator über die Teilstrings zurück. `dlm` kann eines der Formate sein, die als erstes Argument von [`findnext`](@ref) erlaubt sind (d.h. als Zeichenkette, regulärer Ausdruck oder Funktion), oder als einzelnes Zeichen oder Sammlung von Zeichen.

Wenn `dlm` weggelassen wird, wird standardmäßig [`isspace`](@ref) verwendet.

Die optionalen Schlüsselwortargumente sind:

  * `limit`: die maximale Größe des Ergebnisses. `limit=0` bedeutet keine maximale Größe (Standard)
  * `keepempty`: ob leere Felder im Ergebnis beibehalten werden sollen. Standard ist `false` ohne ein `dlm`-Argument, `true` mit einem `dlm`-Argument.

Siehe auch [`split`](@ref).

!!! compat "Julia 1.8"
    Die Funktion `eachsplit` erfordert mindestens Julia 1.8.


# Beispiele

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> b = eachsplit(a, ".")
Base.SplitIterator{String, String}("Ma.rch", ".", 0, true)

julia> collect(b)
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
