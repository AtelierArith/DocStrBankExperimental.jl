```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

`A`에서 길이 `n = length(A)`의 무작위 순환 순열을 생성합니다. 선택적 `rng` 인자는 난수 생성기를 지정하며, [Random Numbers](@ref)를 참조하십시오.

여기서 "순환 순열"은 모든 요소가 단일 사이클 내에 존재함을 의미합니다. 만약 `A`가 비어 있지 않다면(`n > 0`), 가능한 순환 순열의 수는 $(n-1)!$이며, 이는 균일하게 샘플링됩니다. 만약 `A`가 비어 있다면, `randcycle!`는 이를 변경하지 않습니다.

[`randcycle`](@ref)는 새로운 벡터를 할당하는 이 함수의 변형입니다.

# 예시

```jldoctest
julia> randcycle!(Xoshiro(123), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 5
 4
 2
 6
 3
 1
```
