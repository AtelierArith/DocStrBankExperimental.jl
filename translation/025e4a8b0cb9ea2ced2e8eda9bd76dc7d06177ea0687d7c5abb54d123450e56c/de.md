```
length(s::AbstractString) -> Int
length(s::AbstractString, i::Integer, j::Integer) -> Int
```

Gibt die Anzahl der Zeichen im String `s` von den Indizes `i` bis `j` zurück.

Dies wird als die Anzahl der Codeeinheitsindizes von `i` bis `j` berechnet, die gültige Zeichenindizes sind. Mit nur einem einzelnen String-Argument wird die Anzahl der Zeichen im gesamten String berechnet. Mit den Argumenten `i` und `j` wird die Anzahl der Indizes zwischen `i` und `j` einschließlich der gültigen Indizes im String `s` berechnet. Neben den gültigen Werten kann `i` den ungültigen Wert `ncodeunits(s) + 1` und `j` den ungültigen Wert `0` annehmen.

!!! note
    Die Zeitkomplexität dieser Operation ist im Allgemeinen linear. Das heißt, es dauert proportional zur Anzahl der Bytes oder Zeichen im String, da der Wert dynamisch gezählt wird. Dies steht im Gegensatz zur Methode für Arrays, die eine konstante Zeitoperation ist.


Siehe auch [`isvalid`](@ref), [`ncodeunits`](@ref), [`lastindex`](@ref), [`thisind`](@ref), [`nextind`](@ref), [`prevind`](@ref).

# Beispiele

```jldoctest
julia> length("jμΛIα")
5
```
