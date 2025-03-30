```
parentindices(A)
```

[`parent`](@ref)에 해당하는 인덱스를 반환합니다 `A`의 뷰.

# 예제

```jldoctest
julia> A = [1 2; 3 4];

julia> V = view(A, 1, :)
2-element view(::Matrix{Int64}, 1, :) with eltype Int64:
 1
 2

julia> parentindices(V)
(1, Base.Slice(Base.OneTo(2)))
```
