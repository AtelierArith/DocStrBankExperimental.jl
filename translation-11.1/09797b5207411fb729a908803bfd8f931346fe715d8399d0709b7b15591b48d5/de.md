```
stack(f, args...; [dims])
```

Wenden Sie eine Funktion auf jedes Element einer Sammlung an und `stack` das Ergebnis. Oder auf mehrere Sammlungen, die [`zip`](@ref)ped zusammen.

Die Funktion sollte Arrays (oder Tupel oder andere Iteratoren) zurückgeben, die alle die gleiche Größe haben. Diese werden zu Schnitten des Ergebnisses, die entlang von `dims` (sofern angegeben) oder standardmäßig entlang der letzten Dimensionen getrennt sind.

Siehe auch [`mapslices`](@ref), [`eachcol`](@ref).

# Beispiele

```jldoctest
julia> stack(c -> (c, c-32), "julia")
2×5 Matrix{Char}:
 'j'  'u'  'l'  'i'  'a'
 'J'  'U'  'L'  'I'  'A'

julia> stack(eachrow([1 2 3; 4 5 6]), (10, 100); dims=1) do row, n
         vcat(row, row .* n, row ./ n)
       end
2×9 Matrix{Float64}:
 1.0  2.0  3.0   10.0   20.0   30.0  0.1   0.2   0.3
 4.0  5.0  6.0  400.0  500.0  600.0  0.04  0.05  0.06
```
