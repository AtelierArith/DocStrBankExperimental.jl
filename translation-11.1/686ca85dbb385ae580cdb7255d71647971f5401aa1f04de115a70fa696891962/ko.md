```
Base.isambiguous(m1, m2; ambiguous_bottom=false) -> Bool
```

두 메서드 `m1`과 `m2`가 어떤 호출 서명에 대해 모호할 수 있는지 여부를 결정합니다. 이 테스트는 동일한 함수의 다른 메서드의 맥락에서 수행됩니다. 독립적으로 `m1`과 `m2`는 모호할 수 있지만, 모호성을 해결하는 세 번째 메서드가 정의되어 있다면, 이 함수는 `false`를 반환합니다. 또는 독립적으로 `m1`과 `m2`가 정렬될 수 있지만, 세 번째 메서드가 이들과 함께 정렬될 수 없다면, 이들은 함께 모호성을 초래할 수 있습니다.

매개변수 유형의 경우, `ambiguous_bottom` 키워드 인자는 `Union{}`가 유형 매개변수의 모호한 교차점으로 간주되는지 여부를 제어합니다. `true`일 때는 모호한 것으로 간주되고, `false`일 때는 그렇지 않습니다.

# 예제

```jldoctest
julia> foo(x::Complex{<:Integer}) = 1
foo (generic function with 1 method)

julia> foo(x::Complex{<:Rational}) = 2
foo (generic function with 2 methods)

julia> m1, m2 = collect(methods(foo));

julia> typeintersect(m1.sig, m2.sig)
Tuple{typeof(foo), Complex{Union{}}}

julia> Base.isambiguous(m1, m2, ambiguous_bottom=true)
true

julia> Base.isambiguous(m1, m2, ambiguous_bottom=false)
false
```
