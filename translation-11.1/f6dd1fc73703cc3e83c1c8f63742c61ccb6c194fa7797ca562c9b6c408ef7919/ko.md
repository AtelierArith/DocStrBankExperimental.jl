```
uuid4([rng::AbstractRNG]) -> UUID
```

버전 4 (무작위 또는 의사 무작위) 전역 고유 식별자(UUID)를 생성합니다. 이는 RFC 4122에 의해 지정됩니다.

`uuid4`에서 사용되는 기본 rng는 `Random.default_rng()`가 아니며, 인수 없이 `uuid4()`를 호출할 경우 고유 식별자를 반환할 것으로 예상해야 합니다. 중요하게도, `uuid4`의 출력은 `Random.seed!(seed)`가 호출되더라도 반복되지 않습니다. 현재(Julia 1.6 기준) `uuid4`는 기본 rng로 `Random.RandomDevice`를 사용합니다. 그러나 이는 향후 변경될 수 있는 구현 세부사항입니다.

!!! compat "Julia 1.6"
    `uuid4`의 출력은 Julia 1.6 기준으로 `Random.default_rng()`에 의존하지 않습니다.


# 예제

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")
```
