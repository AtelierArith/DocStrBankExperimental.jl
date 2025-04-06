```
seed!([rng=default_rng()], seed) -> rng
seed!([rng=default_rng()]) -> rng
```

난수 생성기를 다시 시드합니다: `rng`는 `seed`가 제공될 때만 재현 가능한 숫자 시퀀스를 제공합니다. 일부 RNG는 `RandomDevice`와 같이 시드를 허용하지 않습니다. `seed!` 호출 후, `rng`는 동일한 시드로 초기화된 새로 생성된 객체와 동등합니다. 허용되는 시드의 유형은 `rng`의 유형에 따라 다르지만, 일반적으로 정수 시드는 작동해야 합니다.

`rng`가 지정되지 않으면 공유 작업 로컬 생성기의 상태를 시드하는 것으로 기본 설정됩니다.

# 예제

```julia-repl
julia> Random.seed!(1234);

julia> x1 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> Random.seed!(1234);

julia> x2 = rand(2)
2-element Vector{Float64}:
 0.32597672886359486
 0.5490511363155669

julia> x1 == x2
true

julia> rng = Xoshiro(1234); rand(rng, 2) == x1
true

julia> Xoshiro(1) == Random.seed!(rng, 1)
true

julia> rand(Random.seed!(rng), Bool) # 재현 불가능
true

julia> rand(Random.seed!(rng), Bool) # 재현 불가능
false

julia> rand(Xoshiro(), Bool) # 재현 불가능
true
```
