```
x | y
```

비트wise or. [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 구현하며, 한 피연산자가 `missing`이고 다른 피연산자가 `false`인 경우 [`missing`](@ref)를 반환합니다.

참고: [`&`](@ref), [`xor`](@ref), [`||`](@ref).

# 예제

```jldoctest
julia> 4 | 10
14

julia> 4 | 1
5

julia> true | missing
true

julia> false | missing
missing
```
