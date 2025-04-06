```
rstrip([pred=isspace,] str::AbstractString) -> SubString
rstrip(str::AbstractString, chars) -> SubString
```

Entfernt nachfolgende Zeichen von `str`, entweder die, die durch `chars` angegeben sind, oder die, für die die Funktion `pred` `true` zurückgibt.

Das Standardverhalten besteht darin, nachfolgende Leerzeichen und Trennzeichen zu entfernen: siehe [`isspace`](@ref) für genaue Details.

Das optionale Argument `chars` gibt an, welche Zeichen entfernt werden sollen: es kann ein einzelnes Zeichen oder ein Vektor oder eine Menge von Zeichen sein.

Siehe auch [`strip`](@ref) und [`lstrip`](@ref).

# Beispiele

```jldoctest
julia> a = rpad("März", 20)
"März               "

julia> rstrip(a)
"März"
```
