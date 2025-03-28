```
DateTime(dt::AbstractString, format::AbstractString; locale="deutsch") -> DateTime
```

Konstruiere ein `DateTime`, indem der `dt` Datumszeit-String gemäß dem Muster im `format`-String geparst wird (siehe [`DateFormat`](@ref) für die Syntax).

!!! Hinweis     Diese Methode erstellt jedes Mal ein `DateFormat`-Objekt, wenn sie aufgerufen wird. Es wird empfohlen, stattdessen ein [`DateFormat`](@ref) Objekt zu erstellen und dieses als zweiten Parameter zu verwenden, um Leistungsverluste bei wiederholter Verwendung des gleichen Formats zu vermeiden.

# Beispiele

```jldoctest
julia> DateTime("2020-01-01", "yyyy-mm-dd")
2020-01-01T00:00:00

julia> a = ("2020-01-01", "2020-01-02");

julia> [DateTime(d, dateformat"yyyy-mm-dd") for d ∈ a] # bevorzugt
2-element Vector{DateTime}:
 2020-01-01T00:00:00
 2020-01-02T00:00:00
```
