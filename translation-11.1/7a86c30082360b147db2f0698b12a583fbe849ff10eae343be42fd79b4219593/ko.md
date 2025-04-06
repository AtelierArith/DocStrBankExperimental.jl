```
Xoshiro(seed::Union{Integer, AbstractString})
Xoshiro()
```

Xoshiro256++는 David Blackman과 Sebastiano Vigna가 "Scrambled Linear Pseudorandom Number Generators", ACM Trans. Math. Softw., 2021에서 설명한 빠른 의사 난수 생성기입니다. 참조 구현은 https://prng.di.unimi.it 에서 사용할 수 있습니다.

높은 속도 외에도 Xoshiro는 메모리 사용량이 적어 오랜 시간 동안 여러 다른 난수 상태를 유지해야 하는 애플리케이션에 적합합니다.

Julia의 Xoshiro 구현은 대량 생성 모드를 가지고 있습니다. 이 모드는 부모로부터 새로운 가상 PRNG를 시드하고 SIMD를 사용하여 병렬로 생성합니다(즉, 대량 스트림은 여러 개의 교차된 xoshiro 인스턴스로 구성됩니다). 가상 PRNG는 대량 요청이 처리되면 폐기되며(힙 할당을 유발하지 않아야 함) 됩니다.

시드가 제공되지 않으면 시스템의 엔트로피를 사용하여 무작위로 생성된 시드가 생성됩니다. 이미 존재하는 `Xoshiro` 객체의 시드를 다시 설정하려면 [`seed!`](@ref) 함수를 참조하십시오.

!!! compat "Julia 1.11"
    음수 정수 시드를 전달하려면 최소한 Julia 1.11이 필요합니다.


# 예제

```jldoctest
julia> using Random

julia> rng = Xoshiro(1234);

julia> x1 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> rng = Xoshiro(1234);

julia> x2 = rand(rng, 2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true
```
