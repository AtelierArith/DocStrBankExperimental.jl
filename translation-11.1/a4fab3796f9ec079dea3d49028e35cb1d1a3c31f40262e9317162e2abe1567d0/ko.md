```
typeof(x)
```

`x`의 구체적인 타입을 가져옵니다.

자세한 내용은 [`eltype`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> a = 1//2;

julia> typeof(a)
Rational{Int64}

julia> M = [1 2; 3.5 4];

julia> typeof(M)
Matrix{Float64} (alias for Array{Float64, 2})
```
