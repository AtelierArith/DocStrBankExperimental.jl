```
uuid5(ns::UUID, name::String) -> UUID
```

버전 5(네임스페이스 및 도메인 기반) 범용 고유 식별자(UUID)를 생성합니다. 이는 RFC 4122에 명시되어 있습니다.

!!! compat "Julia 1.1"
    이 함수는 최소한 Julia 1.1이 필요합니다.


# 예제

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> u4 = uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")

julia> u5 = uuid5(u4, "julia")
UUID("2df91e3f-da06-5362-a6fe-03772f2e14c9")
```
