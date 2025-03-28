```
map(f, A::AbstractArray...) -> N-array
```

Wenn man auf mehrdimensionale Arrays mit derselben [`ndims`](@ref) wirkt, müssen sie alle dieselben [`axes`](@ref) haben, und das Ergebnis wird ebenfalls so sein.

Siehe auch [`broadcast`](@ref), das unterschiedliche Größen erlaubt.

# Beispiele

```
julia> map(//, [1 2; 3 4], [4 3; 2 1])
2×2 Matrix{Rational{Int64}}:
 1//4  2//3
 3//2  4//1

julia> map(+, [1 2; 3 4], zeros(2,1))
ERROR: DimensionMismatch

julia> map(+, [1 2; 3 4], [1,10,100,1000], zeros(3,1))  # iteriert, bis das 3. erschöpft ist
3-element Vector{Float64}:
   2.0
  13.0
 102.0
```
