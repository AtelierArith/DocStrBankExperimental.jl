```
Meta.quot(ex)::Expr
```

표현식 `ex`를 인용하여 머리 `quote`가 있는 표현식을 생성합니다. 이는 예를 들어 AST에서 `Expr` 유형의 객체를 나타내는 데 사용할 수 있습니다. [QuoteNode](@ref man-quote-node)에 대한 매뉴얼 섹션도 참조하십시오.

# 예제

```jldoctest
julia> eval(Meta.quot(:x))
:x

julia> dump(Meta.quot(:x))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Symbol x

julia> eval(Meta.quot(:(1+2)))
:(1 + 2)
```
