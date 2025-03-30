```
Expr(head::Symbol, args...)
```

구문 분석된 줄리아 코드(AST)에서 복합 표현을 나타내는 유형입니다. 각 표현은 어떤 종류의 표현인지 식별하는 `head` `Symbol`(예: 호출, for 루프, 조건문 등)과 하위 표현(예: 호출의 인수)으로 구성됩니다. 하위 표현은 `args`라는 `Vector{Any}` 필드에 저장됩니다.

[메타프로그래밍](@ref) 장과 개발자 문서 [줄리아 ASTs](@ref)를 참조하세요.

# 예제

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```
