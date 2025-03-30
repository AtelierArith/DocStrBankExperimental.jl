```
MersenneTwister(seed)
MersenneTwister()
```

`MersenneTwister` RNG 객체를 생성합니다. 서로 다른 RNG 객체는 고유한 시드를 가질 수 있으며, 이는 서로 다른 난수 스트림을 생성하는 데 유용할 수 있습니다. `seed`는 정수, 문자열 또는 `UInt32` 정수의 벡터일 수 있습니다. 시드가 제공되지 않으면 무작위로 생성된 시드가 생성됩니다(시스템의 엔트로피를 사용하여). 이미 존재하는 `MersenneTwister` 객체의 시드를 다시 설정하려면 [`seed!`](@ref) 함수를 참조하십시오.

!!! compat "Julia 1.11"
    음수 정수 시드를 전달하려면 최소한 Julia 1.11이 필요합니다.


# 예제

```jldoctest
julia> rng = MersenneTwister(123);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x2 = rand(MersenneTwister(123), 2)
2-element Vector{Float64}:
 0.37453777969575874
 0.8735343642013971

julia> x1 == x2
true
```
