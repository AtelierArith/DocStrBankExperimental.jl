```
nand(x, y)
⊼(x, y)
```

`x`와 `y`의 비트 단위 nand(논리곱의 부정). [삼값 논리](https://en.wikipedia.org/wiki/Three-valued_logic)를 구현하며, 인수 중 하나가 `missing`인 경우 [`missing`](@ref)를 반환합니다.

중위 연산 `a ⊼ b`는 `nand(a,b)`의 동의어이며, `⊼`는 Julia REPL에서 `\nand` 또는 `\barwedge`를 탭 완성하여 입력할 수 있습니다.

# 예제

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
