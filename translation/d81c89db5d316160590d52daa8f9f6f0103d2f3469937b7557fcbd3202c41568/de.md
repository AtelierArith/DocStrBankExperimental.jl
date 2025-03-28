```
strip([pred=isspace,] str::AbstractString) -> SubString
strip(str::AbstractString, chars) -> SubString
```

Entfernt führende und nachfolgende Zeichen aus `str`, entweder die, die durch `chars` angegeben sind, oder die, für die die Funktion `pred` `true` zurückgibt.

Das Standardverhalten besteht darin, führende und nachfolgende Leerzeichen und Trennzeichen zu entfernen: siehe [`isspace`](@ref) für genaue Details.

Das optionale Argument `chars` gibt an, welche Zeichen entfernt werden sollen: es kann ein einzelnes Zeichen, ein Vektor oder eine Menge von Zeichen sein.

Siehe auch [`lstrip`](@ref) und [`rstrip`](@ref).

!!! compat "Julia 1.2"
    Die Methode, die eine Prädikatsfunktion akzeptiert, erfordert Julia 1.2 oder höher.


# Beispiele

```jldoctest
julia> strip("{3, 5}\n", ['{', '}', '\n'])
"3, 5"
```
