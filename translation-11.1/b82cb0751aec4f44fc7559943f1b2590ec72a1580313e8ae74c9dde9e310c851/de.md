```
broadcast!(f, dest, As...)
```

Wie [`broadcast`](@ref), aber speichert das Ergebnis von `broadcast(f, As...)` im `dest`-Array. Beachten Sie, dass `dest` nur verwendet wird, um das Ergebnis zu speichern, und keine Argumente an `f` liefert, es sei denn, es ist auch in den `As` aufgeführt, wie in `broadcast!(f, A, A, B)`, um `A[:] = broadcast(f, A, B)` auszuführen.

# Beispiele

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
