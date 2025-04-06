```
imag(A::AbstractArray)
```

Gibt ein Array zurück, das den Imaginärteil jedes Eintrags im Array `A` enthält.

Entspricht `imag.(A)`, es sei denn, `A` hat null Dimensionen, in diesem Fall wird ein 0-dimensionales Array zurückgegeben (anstatt eines Skalars).

# Beispiele

```jldoctest
julia> imag([1, 2im, 3 + 4im])
3-element Vector{Int64}:
 0
 2
 4

julia> imag(fill(2 - im))
0-dimensional Array{Int64, 0}:
-1
```
