```
broadcast!(f, dest, As...)
```

[`broadcast`](@ref) gibi, ancak `broadcast(f, As...)` sonucunu `dest` dizisinde saklar. `dest` yalnızca sonucu saklamak için kullanılır ve `f`'ye argüman sağlamaz, yalnızca `As` içinde listelenmişse, örneğin `broadcast!(f, A, A, B)` ile `A[:] = broadcast(f, A, B)` işlemini gerçekleştirmek için.

# Örnekler

```jldoctest
julia> A = [1.0; 0.0]; B = [0.0; 0.0];

julia> broadcast!(+, B, A, (0, -2.0));

julia> B
2-element Vector{Float64}:
  1.0
 -2.0

julia> A
2-element Vector{Float64}:
 1.0
 0.0

julia> broadcast!(+, A, A, (0, -2.0));

julia> A
2-element Vector{Float64}:
  1.0
 -2.0
```
