```
randexp([rng=default_rng()], [T=Float64], [dims...])
```

1의 스케일을 가진 지수 분포에 따라 타입 `T`의 난수를 생성합니다. 선택적으로 이러한 난수의 배열을 생성할 수 있습니다. `Base` 모듈은 현재 [`Float16`](@ref), [`Float32`](@ref), 및 [`Float64`](@ref) (기본값) 타입에 대한 구현을 제공합니다.

# 예제

```jldoctest
julia> rng = Xoshiro(123);

julia> randexp(rng, Float32)
1.1757717f0

julia> randexp(rng, 3, 3)
3×3 Matrix{Float64}:
 1.37766  0.456653  0.236418
 3.40007  0.229917  0.0684921
 0.48096  0.577481  0.71835
```
