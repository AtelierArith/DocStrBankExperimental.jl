```
size(A::AbstractArray, [dim])
```

Gibt ein Tupel zurück, das die Dimensionen von `A` enthält. Optional können Sie eine Dimension angeben, um nur die Länge dieser Dimension zu erhalten.

Beachten Sie, dass `size` möglicherweise nicht für Arrays mit nicht standardmäßigen Indizes definiert ist, in diesem Fall kann [`axes`](@ref) nützlich sein. Siehe das Handbuchkapitel über [Arrays mit benutzerdefinierten Indizes](@ref man-custom-indices).

Siehe auch: [`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref).

# Beispiele

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
