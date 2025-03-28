```
Time(t::AbstractString, format::AbstractString; locale="deutsch") -> Time
```

Konstruiere eine `Time`, indem der `t` Zeitstring gemäß dem Muster im `format` String geparst wird (siehe [`DateFormat`](@ref) für die Syntax).

!!! Hinweis     Diese Methode erstellt jedes Mal ein `DateFormat` Objekt, wenn sie aufgerufen wird. Es wird empfohlen, stattdessen ein [`DateFormat`](@ref) Objekt zu erstellen und dieses als zweiten Parameter zu verwenden, um Leistungsverluste bei wiederholter Verwendung des gleichen Formats zu vermeiden.

# Beispiele

```jldoctest
julia> Time("12:34pm", "HH:MMp")
12:34:00

julia> a = ("12:34pm", "2:34am");

julia> [Time(d, dateformat"HH:MMp") for d ∈ a] # bevorzugt
2-element Vector{Time}:
 12:34:00
 02:34:00
```
