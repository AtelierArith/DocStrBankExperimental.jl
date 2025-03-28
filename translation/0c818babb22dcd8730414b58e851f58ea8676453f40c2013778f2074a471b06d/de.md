```
promote_shape(s1, s2)
```

Überprüfen Sie die Kompatibilität von zwei Array-Formen, wobei nachfolgende Singleton-Dimensionen erlaubt sind, und geben Sie die Form mit mehr Dimensionen zurück.

# Beispiele

```jldoctest
julia> a = fill(1, (3,4,1,1,1));

julia> b = fill(1, (3,4));

julia> promote_shape(a,b)
(Base.OneTo(3), Base.OneTo(4), Base.OneTo(1), Base.OneTo(1), Base.OneTo(1))

julia> promote_shape((2,3,1,4), (2, 3, 1, 4, 1))
(2, 3, 1, 4, 1)
```
