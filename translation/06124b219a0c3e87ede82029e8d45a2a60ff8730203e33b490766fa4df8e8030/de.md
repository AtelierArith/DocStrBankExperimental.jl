```
transcode(T, src)
```

Konvertieren Sie Zeichendaten zwischen Unicode-Codierungen. `src` ist entweder ein `String` oder ein `Vector{UIntXX}` von UTF-XX-Codeeinheiten, wobei `XX` 8, 16 oder 32 ist. `T` gibt die Codierung des Rückgabewerts an: `String`, um einen (UTF-8-codierten) `String` zurückzugeben, oder `UIntXX`, um einen `Vector{UIntXX}` von UTF-`XX`-Daten zurückzugeben. (Das Alias [`Cwchar_t`](@ref) kann ebenfalls als Ganzzahltyp verwendet werden, um `wchar_t*`-Strings zu konvertieren, die von externen C-Bibliotheken verwendet werden.)

Die Funktion `transcode` ist erfolgreich, solange die Eingabedaten vernünftig in der Zielcodierung dargestellt werden können; sie ist immer erfolgreich für Konvertierungen zwischen UTF-XX-Codierungen, selbst für ungültige Unicode-Daten.

Derzeit wird nur die Konvertierung zu/von UTF-8 unterstützt.

# Beispiele

```jldoctest
julia> str = "αβγ"
"αβγ"

julia> transcode(UInt16, str)
3-element Vector{UInt16}:
 0x03b1
 0x03b2
 0x03b3

julia> transcode(String, transcode(UInt16, str))
"αβγ"
```
