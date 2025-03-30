```
randperm([rng=default_rng(),] n::Integer)
```

길이 `n`의 무작위 순열을 생성합니다. 선택적 `rng` 인자는 무작위 수 생성기를 지정합니다(자세한 내용은 [무작위 수](@ref) 참조). 결과의 요소 유형은 `n`의 유형과 동일합니다.

임의의 벡터를 무작위로 섞으려면 [`shuffle`](@ref) 또는 [`shuffle!`](@ref)를 참조하세요.

!!! compat "Julia 1.1"
    Julia 1.1에서는 `randperm`이 `eltype(v) == typeof(n)`인 벡터 `v`를 반환하는 반면, Julia 1.0에서는 `eltype(v) == Int`입니다.


# 예제

```jldoctest
julia> randperm(Xoshiro(123), 4)
4-element Vector{Int64}:
 1
 4
 2
 3
```
