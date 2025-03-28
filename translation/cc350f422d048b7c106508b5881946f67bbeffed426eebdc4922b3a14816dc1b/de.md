```
lstrip([pred=isspace,] str::AbstractString) -> SubString
lstrip(str::AbstractString, chars) -> SubString
```

Entfernt führende Zeichen aus `str`, entweder die, die durch `chars` angegeben sind, oder die, für die die Funktion `pred` `true` zurückgibt.

Das Standardverhalten besteht darin, führende Leerzeichen und Trennzeichen zu entfernen: siehe [`isspace`](@ref) für genaue Details.

Das optionale Argument `chars` gibt an, welche Zeichen entfernt werden sollen: es kann ein einzelnes Zeichen oder ein Vektor oder eine Menge von Zeichen sein.

Siehe auch [`strip`](@ref) und [`rstrip`](@ref).

# Beispiele

```jldoctest
julia> a = lpad("März", 20)
"               März"

julia> lstrip(a)
"März"
```
