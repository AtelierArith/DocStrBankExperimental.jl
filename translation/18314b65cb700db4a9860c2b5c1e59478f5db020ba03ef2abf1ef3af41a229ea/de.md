```
fill(value, dims::Tuple)
fill(value, dims...)
```

Erstellt ein Array der Größe `dims`, wobei jeder Ort auf `value` gesetzt ist.

Zum Beispiel gibt `fill(1.0, (5,5))` ein 5×5-Array von Fließkommazahlen zurück, mit `1.0` an jedem Ort des Arrays.

Die Längen der Dimensionen `dims` können entweder als Tuple oder als eine Sequenz von Argumenten angegeben werden. Ein `N`-längiges Tuple oder `N` Argumente, die dem `value` folgen, spezifizieren ein `N`-dimensionales Array. Daher ist ein gängiges Idiom zur Erstellung eines null-dimensionalen Arrays, dessen einziger Ort auf `x` gesetzt ist, `fill(x)`.

Jeder Ort des zurückgegebenen Arrays ist auf (und ist somit [`===`](@ref) zu) dem `value` gesetzt, das übergeben wurde; das bedeutet, dass, wenn das `value` selbst geändert wird, alle Elemente des gefüllten Arrays diese Änderung widerspiegeln, weil sie *immer noch* genau dieses `value` sind. Dies ist bei `fill(1.0, (5,5))` unbedenklich, da das `value` `1.0` unveränderlich ist und nicht selbst geändert werden kann, kann jedoch bei veränderlichen Werten wie – am häufigsten – Arrays unerwartet sein. Zum Beispiel platziert `fill([], 3)` *das genau gleiche* leere Array an allen drei Orten des zurückgegebenen Vektors:

```jldoctest
julia> v = fill([], 3)
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v[1] === v[2] === v[3]
true

julia> value = v[1]
Any[]

julia> push!(value, 867_5309)
1-element Vector{Any}:
 8675309

julia> v
3-element Vector{Vector{Any}}:
 [8675309]
 [8675309]
 [8675309]
```

Um ein Array mit vielen unabhängigen inneren Arrays zu erstellen, verwenden Sie stattdessen eine [Komprehension](@ref man-comprehensions). Dies erstellt bei jeder Iteration der Schleife ein neues und distinct Array:

```jldoctest
julia> v2 = [[] for _ in 1:3]
3-element Vector{Vector{Any}}:
 []
 []
 []

julia> v2[1] === v2[2] === v2[3]
false

julia> push!(v2[1], 8675309)
1-element Vector{Any}:
 8675309

julia> v2
3-element Vector{Vector{Any}}:
 [8675309]
 []
 []
```

Siehe auch: [`fill!`](@ref), [`zeros`](@ref), [`ones`](@ref), [`similar`](@ref).

# Beispiele

```jldoctest
julia> fill(1.0, (2,3))
2×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0

julia> fill(42)
0-dimensional Array{Int64, 0}:
42

julia> A = fill(zeros(2), 2) # setzt beide Elemente auf den gleichen [0.0, 0.0] Vektor
2-element Vector{Vector{Float64}}:
 [0.0, 0.0]
 [0.0, 0.0]

julia> A[1][1] = 42; # ändert den gefüllten Wert auf [42.0, 0.0]

julia> A # sowohl A[1] als auch A[2] sind der genau gleiche Vektor
2-element Vector{Vector{Float64}}:
 [42.0, 0.0]
 [42.0, 0.0]
```
