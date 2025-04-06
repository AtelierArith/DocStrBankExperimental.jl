```
ncodeunits(s::AbstractString) -> Int
```

Gibt die Anzahl der Codeeinheiten in einem String zurück. Indizes, die im Bereich liegen, um auf diesen String zuzugreifen, müssen `1 ≤ i ≤ ncodeunits(s)` erfüllen. Nicht alle solchen Indizes sind gültig – sie können nicht der Anfang eines Zeichens sein, aber sie geben einen Codeeinheitswert zurück, wenn `codeunit(s,i)` aufgerufen wird.

# Beispiele

```jldoctest
julia> ncodeunits("The Julia Language")
18

julia> ncodeunits("∫eˣ")
6

julia> ncodeunits('∫'), ncodeunits('e'), ncodeunits('ˣ')
(3, 1, 2)
```

Siehe auch [`codeunit`](@ref), [`checkbounds`](@ref), [`sizeof`](@ref), [`length`](@ref), [`lastindex`](@ref).
