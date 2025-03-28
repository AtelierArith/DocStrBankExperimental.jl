```
reinterpret(T::DataType, A::AbstractArray)
```

Construit une vue de l'array avec les mêmes données binaires que l'array donné, mais avec `T` comme type d'élément.

Cette fonction fonctionne également sur les arrays "paresseux" dont les éléments ne sont pas calculés tant qu'ils ne sont pas explicitement récupérés. Par exemple, `reinterpret` sur la plage `1:6` fonctionne de manière similaire à sur le vecteur dense `collect(1:6)` :

```jldoctest
julia> reinterpret(Float32, UInt32[1 2 3 4 5])
1×5 reinterpret(Float32, ::Matrix{UInt32}):
 1.0f-45  3.0f-45  4.0f-45  6.0f-45  7.0f-45

julia> reinterpret(Complex{Int}, 1:6)
3-element reinterpret(Complex{Int64}, ::UnitRange{Int64}):
 1 + 2im
 3 + 4im
 5 + 6im
```

Si l'emplacement des bits de remplissage ne s'aligne pas entre `T` et `eltype(A)`, l'array résultant sera en lecture seule ou en écriture seule, pour empêcher des bits invalides d'être écrits ou lus, respectivement.

```jldoctest
julia> a = reinterpret(Tuple{UInt8, UInt32}, UInt32[1, 2])
1-element reinterpret(Tuple{UInt8, UInt32}, ::Vector{UInt32}):
 (0x01, 0x00000002)

julia> a[1] = 3
ERROR: Padding of type Tuple{UInt8, UInt32} is not compatible with type UInt32.

julia> b = reinterpret(UInt32, Tuple{UInt8, UInt32}[(0x01, 0x00000002)]); # showing will error

julia> b[1]
ERROR: Padding of type UInt32 is not compatible with type Tuple{UInt8, UInt32}.
```
