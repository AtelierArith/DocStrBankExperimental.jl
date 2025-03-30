```
endswith(suffix)
```

`suffix`로 끝나는지 확인하는 함수를 만듭니다. 즉, `y -> endswith(y, suffix)`와 동등한 함수입니다.

반환된 함수는 `Base.Fix2{typeof(endswith)}` 유형이며, 이는 특수화된 메서드를 구현하는 데 사용할 수 있습니다.

!!! compat "Julia 1.5"
    단일 인수 `endswith(suffix)`는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> endswith("Julia")("Ends with Julia")
true

julia> endswith("Julia")("JuliaLang")
false
```
