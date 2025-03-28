```
circcopy!(dest, src)
```

Copie `src` dans `dest`, en indexant chaque dimension modulo sa longueur. `src` et `dest` doivent avoir la même taille, mais peuvent être décalés dans leurs indices ; tout décalage entraîne un retour circulaire. Si les tableaux ont des indices qui se chevauchent, alors sur le domaine du chevauchement, `dest` est identique à `src`.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


Voir aussi : [`circshift`](@ref).

# Exemples

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} with indices 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
