```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

주어진 제네릭 함수가 주어진 `Tuple`의 인수 유형과 일치하는 메서드를 가지고 있는지 확인합니다. 이때 `world`로 주어진 세계의 나이의 상한이 적용됩니다.

키워드 인수 이름의 튜플 `kwnames`가 제공되면, 이는 또한 `f`의 메서드가 `t`와 일치하는지와 주어진 키워드 인수 이름을 가지고 있는지 확인합니다. 일치하는 메서드가 가변 개수의 키워드 인수를 허용하는 경우, 예를 들어 `kwargs...`와 같이, `kwnames`에 주어진 이름은 유효한 것으로 간주됩니다. 그렇지 않으면 제공된 이름은 메서드의 키워드 인수의 부분 집합이어야 합니다.

자세한 내용은 [`applicable`](@ref)를 참조하십시오.

!!! compat "Julia 1.2"
    키워드 인수 이름을 제공하려면 Julia 1.2 이상이 필요합니다.


# 예제

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g는 임의의 kwargs를 허용합니다
true
```
