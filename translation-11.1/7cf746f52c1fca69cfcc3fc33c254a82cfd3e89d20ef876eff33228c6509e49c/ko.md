```
nor(x, y)
⊽(x, y)
```

`x`와 `y`의 비트 단위 nor (not or). [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 구현하며, 인수 중 하나가 `missing`이고 다른 하나가 `true`가 아닐 경우 [`missing`](@ref)를 반환합니다.

중위 연산 `a ⊽ b`는 `nor(a,b)`의 동의어이며, `⊽`는 Julia REPL에서 `\nor` 또는 `\barvee`를 탭 완성하여 입력할 수 있습니다.

# 예제

```jldoctest
julia> nor(true, false)
false

julia> nor(true, true)
false

julia> nor(true, missing)
false

julia> false ⊽ false
true

julia> false ⊽ missing
missing

julia> [true; true; false] .⊽ [true; false; false]
3-element BitVector:
 0
 0
 1
```
