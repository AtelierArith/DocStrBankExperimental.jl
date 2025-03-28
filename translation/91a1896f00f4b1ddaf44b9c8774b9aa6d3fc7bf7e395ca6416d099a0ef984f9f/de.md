```
@views Ausdruck
```

Konvertiere jede Array-Slicing-Operation im gegebenen Ausdruck (der ein `begin`/`end`-Block, eine Schleife, eine Funktion usw. sein kann) so, dass eine Ansicht zurückgegeben wird. Skalare Indizes, Nicht-Array-Typen und explizite [`getindex`](@ref)-Aufrufe (im Gegensatz zu `array[...]`) sind nicht betroffen.

Ähnlich konvertiert `@views` String-Slices in [`SubString`](@ref)-Ansichten.

!!! Hinweis     Das `@views`-Makro betrifft nur `array[...]`-Ausdrücke, die explizit im gegebenen `Ausdruck` erscheinen, nicht das Array-Slicing, das in von diesem Code aufgerufenen Funktionen auftritt.

!!! Kompatibilität "Julia 1.5"     Die Verwendung von `begin` in einem Indexausdruck, um auf den ersten Index zu verweisen, wurde in Julia 1.4 implementiert, wurde jedoch erst ab Julia 1.5 von `@views` unterstützt.

# Beispiele

```jldoctest
julia> A = zeros(3, 3);

julia> @views for row in 1:3
           b = A[row, :] # b ist eine Ansicht, kein Kopie
           b .= row      # weise jedem Element den Zeilenindex zu
       end

julia> A
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 2.0  2.0  2.0
 3.0  3.0  3.0
```
