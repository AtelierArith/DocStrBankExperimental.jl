```
findlast(ch::AbstractChar, string::AbstractString)
```

문자 `ch`의 마지막 발생을 `string`에서 찾습니다.

!!! compat "Julia 1.3"
    이 메서드는 최소한 Julia 1.3이 필요합니다.


# 예제

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
