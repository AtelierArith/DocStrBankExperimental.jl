```
x & y
```

비트 단위 AND. [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 구현하며, 한 피연산자가 `missing`이고 다른 피연산자가 `true`인 경우 [`missing`](@ref)를 반환합니다. 함수 적용 형태를 위해 괄호를 추가하세요: `(&)(x, y)`.

또한: [`|`](@ref), [`xor`](@ref), [`&&`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> 4 & 10
0

julia> 4 & 12
4

julia> true & missing
missing

julia> false & missing
false
```
