```
broadcast!(f, dest, As...)
```

[`broadcast`](@ref)와 유사하지만, `broadcast(f, As...)`의 결과를 `dest` 배열에 저장합니다. `dest`는 결과를 저장하는 데만 사용되며, `As`에 나열되지 않는 한 `f`에 인수를 제공하지 않습니다. 예를 들어 `broadcast!(f, A, A, B)`는 `A[:] = broadcast(f, A, B)`를 수행합니다.

# 예제

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
