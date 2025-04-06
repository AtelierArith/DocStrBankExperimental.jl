```
randstring([rng=default_rng()], [chars], [len=8])
```

길이 `len`의 임의 문자열을 생성하며, `chars`의 문자로 구성됩니다. `chars`는 기본적으로 대문자 및 소문자와 숫자 0-9의 집합으로 설정됩니다. 선택적 `rng` 인자는 난수 생성기를 지정합니다. [Random Numbers](@ref)를 참조하세요.

# 예제

```jldoctest
julia> Random.seed!(3); randstring()
"Lxz5hUwn"

julia> randstring(Xoshiro(3), 'a':'z', 6)
"iyzcsm"

julia> randstring("ACGT")
"TGCTCCTC"
```

!!! 주의     `chars`는 `Char` 또는 `UInt8` 타입의 문자 컬렉션일 수 있으며 (더 효율적), [`rand`](@ref)가 그로부터 임의로 문자를 선택할 수 있어야 합니다.
