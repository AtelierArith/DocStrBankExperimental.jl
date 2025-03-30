```
randcycle([rng=default_rng(),] n::Integer)
```

길이 `n`의 무작위 순환 순열을 생성합니다. 선택적 `rng` 인자는 난수 생성기를 지정하며, [무작위 수](@ref)를 참조하십시오. 결과의 요소 유형은 `n`의 유형과 동일합니다.

여기서 "순환 순열"은 모든 요소가 단일 사이클 내에 존재함을 의미합니다. `n > 0`인 경우, 가능한 순환 순열의 수는 $(n-1)!$이며, 이는 균일하게 샘플링됩니다. `n == 0`인 경우, `randcycle`은 빈 벡터를 반환합니다.

[`randcycle!`](@ref)는 이 함수의 제자리 변형입니다.

!!! compat "Julia 1.1"
    Julia 1.1 이상에서는 `randcycle`이 `eltype(v) == typeof(n)`인 벡터 `v`를 반환하는 반면, Julia 1.0에서는 `eltype(v) == Int`입니다.


# 예제

```jldoctest
julia> randcycle(Xoshiro(123), 6)
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
