```
length(A::AbstractArray)
```

Gibt die Anzahl der Elemente im Array zurück, standardmäßig `prod(size(A))`.

# Beispiele

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
