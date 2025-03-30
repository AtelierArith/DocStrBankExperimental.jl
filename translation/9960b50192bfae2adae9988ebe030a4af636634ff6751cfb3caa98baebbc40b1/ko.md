```
모든 요소가 1인 `Array`를 생성하며, 요소 유형 `T`와 크기는 `dims`로 지정됩니다. [`fill`](@ref), [`zeros`](@ref)도 참조하십시오.

# 예제

```

jldoctest julia> ones(1,2) 1×2 Matrix{Float64}:  1.0  1.0

julia> ones(ComplexF64, 2, 3) 2×3 Matrix{ComplexF64}:  1.0+0.0im  1.0+0.0im  1.0+0.0im  1.0+0.0im  1.0+0.0im  1.0+0.0im

```

```
