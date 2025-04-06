```
Meta.isexpr(ex, head[, n])::Bool
```

`ex`가 주어진 타입 `head`를 가진 `Expr`인 경우 `true`를 반환하며, 선택적으로 인수 목록의 길이가 `n`인 경우도 포함됩니다. `head`는 `Symbol` 또는 `Symbol`의 컬렉션일 수 있습니다. 예를 들어, 매크로에 함수 호출 표현식이 전달되었는지 확인하려면 `isexpr(ex, :call)`을 사용할 수 있습니다.

# 예제

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # 여러 가능한 헤드
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
