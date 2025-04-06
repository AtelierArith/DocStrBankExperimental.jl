```
:expr
```

표현식 `expr`을 인용하여 `expr`의 추상 구문 트리(AST)를 반환합니다. AST는 `Expr`, `Symbol` 또는 리터럴 값일 수 있습니다. 구문 `:identifier`는 `Symbol`으로 평가됩니다.

참고: [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# 예제

```jldoctest
julia> expr = :(a = b + 2*x)
:(a = b + 2x)

julia> sym = :some_identifier
:some_identifier

julia> value = :0xff
0xff

julia> typeof((expr, sym, value))
Tuple{Expr, Symbol, UInt8}
```
