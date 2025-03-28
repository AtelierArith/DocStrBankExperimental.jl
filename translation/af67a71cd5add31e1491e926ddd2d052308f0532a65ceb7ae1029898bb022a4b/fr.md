```
transpose!(dest,src)
```

Transposer le tableau `src` et stocker le résultat dans le tableau préalloué `dest`, qui doit avoir une taille correspondant à `(size(src,2),size(src,1))`. Aucune transposition en place n'est supportée et des résultats inattendus se produiront si `src` et `dest` ont des régions de mémoire qui se chevauchent.

# Exemples

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(Complex{Int64}, 2, 2)
2×2 Matrix{Complex{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> transpose!(B, A);

julia> B
2×2 Matrix{Complex{Int64}}:
 3+2im  8+7im
 9+2im  4+6im

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
