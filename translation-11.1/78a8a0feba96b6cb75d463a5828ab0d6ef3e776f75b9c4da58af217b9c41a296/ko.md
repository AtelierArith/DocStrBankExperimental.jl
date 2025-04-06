```
startswith(prefix)
```

`prefix`로 시작하는지 여부를 확인하는 함수를 만듭니다. 즉, `y -> startswith(y, prefix)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix2{typeof(startswith)}` 유형이며, 이는 특수화된 메서드를 구현하는 데 사용할 수 있습니다.

!!! compat "Julia 1.5"
    단일 인수 `startswith(prefix)`는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> startswith("Julia")("JuliaLang")
true

julia> startswith("Julia")("Ends with Julia")
false
```
