```
split(str::AbstractString, dlm; limit::Integer=0, keepempty::Bool=true)
split(str::AbstractString; limit::Integer=0, keepempty::Bool=false)
```

Teile `str` in ein Array von Teilstrings auf, basierend auf Vorkommen des Trennzeichens `dlm`. `dlm` kann eines der Formate sein, die als erstes Argument von [`findnext`](@ref) erlaubt sind (d.h. als String, regulärer Ausdruck oder Funktion), oder als einzelnes Zeichen oder eine Sammlung von Zeichen.

Wenn `dlm` weggelassen wird, wird standardmäßig [`isspace`](@ref) verwendet.

Die optionalen Schlüsselwortargumente sind:

  * `limit`: die maximale Größe des Ergebnisses. `limit=0` bedeutet keine maximale Größe (Standard)
  * `keepempty`: ob leere Felder im Ergebnis beibehalten werden sollen. Standard ist `false` ohne ein `dlm`-Argument, `true` mit einem `dlm`-Argument.

Siehe auch [`rsplit`](@ref), [`eachsplit`](@ref).

# Beispiele

```jldoctest
julia> a = "Ma.rch"
"Ma.rch"

julia> split(a, ".")
2-element Vector{SubString{String}}:
 "Ma"
 "rch"
```
