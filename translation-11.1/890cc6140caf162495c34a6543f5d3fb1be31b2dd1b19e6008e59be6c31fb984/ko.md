```
!(x)
```

부울 부정. [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 구현하며, `x`가 `missing`인 경우 [`missing`](@ref)를 반환합니다.

비트 단위 부정에 대해서는 [`~`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> !true
false

julia> !false
true

julia> !missing
missing

julia> .![true false true]
1×3 BitMatrix:
 0  1  0
```
