```
UniformScaling{T<:Number}
```

스칼라와 항등 연산자 `λ*I`의 곱으로 정의된 일반 크기의 균일 스케일링 연산자입니다. 명시적인 `size`가 없지만, 많은 경우에 행렬처럼 작동하며 일부 인덱싱을 지원합니다. [`I`](@ref)도 참조하십시오.

!!! compat "Julia 1.6"
    범위를 사용한 인덱싱은 Julia 1.6부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> J = UniformScaling(2.)
UniformScaling{Float64}
2.0*I

julia> A = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> J*A
2×2 Matrix{Float64}:
 2.0  4.0
 6.0  8.0

julia> J[1:2, 1:2]
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
