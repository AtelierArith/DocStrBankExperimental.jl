```
uuid1([rng::AbstractRNG]) -> UUID
```

버전 1(시간 기반) 범용 고유 식별자(UUID)를 생성합니다. 이는 RFC 4122에 명시되어 있습니다. 노드 ID는 RFC의 4.5절에 따라 무작위로 생성되며(호스트를 식별하지 않음) 주의해야 합니다.

`uuid1`에서 사용되는 기본 rng는 `Random.default_rng()`가 아니며, 인수 없이 `uuid1()`을 호출할 경우 고유 식별자를 반환할 것으로 예상해야 합니다. 중요하게도, `uuid1`의 출력은 `Random.seed!(seed)`가 호출되더라도 반복되지 않습니다. 현재(Julia 1.6 기준) `uuid1`은 기본 rng로 `Random.RandomDevice`를 사용합니다. 그러나 이는 향후 변경될 수 있는 구현 세부사항입니다.

!!! compat "Julia 1.6"
    Julia 1.6 기준으로 `uuid1`의 출력은 `Random.default_rng()`에 의존하지 않습니다.


# 예제

```jldoctest; filter = r"[a-z0-9]{8}-([a-z0-9]{4}-){3}[a-z0-9]{12}"
julia> using Random

julia> rng = MersenneTwister(1234);

julia> uuid1(rng)
UUID("cfc395e8-590f-11e8-1f13-43a2532b2fa8")
```
