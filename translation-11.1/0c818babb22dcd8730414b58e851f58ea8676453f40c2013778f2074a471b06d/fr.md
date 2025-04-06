```
promote_shape(s1, s2)
```

Vérifiez la compatibilité de deux formes de tableau, en permettant des dimensions singleton finales, et renvoyez la forme qui a le plus de dimensions.

# Exemples

```jldoctest
julia> a = fill(1, (3,4,1,1,1));

julia> b = fill(1, (3,4));

julia> promote_shape(a,b)
(Base.OneTo(3), Base.OneTo(4), Base.OneTo(1), Base.OneTo(1), Base.OneTo(1))

julia> promote_shape((2,3,1,4), (2, 3, 1, 4, 1))
(2, 3, 1, 4, 1)
```
