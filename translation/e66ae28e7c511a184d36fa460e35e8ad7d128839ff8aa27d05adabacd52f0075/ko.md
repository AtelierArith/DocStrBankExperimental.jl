```
ComposedFunction{Outer,Inner} <: Function
```

두 개의 호출 가능한 객체 `outer::Outer`와 `inner::Inner`의 조합을 나타냅니다. 즉,

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

`ComposedFunction`의 인스턴스를 구성하는 선호되는 방법은 조합 연산자 [`∘`](@ref)를 사용하는 것입니다:

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

조합된 조각들은 `ComposedFunction`의 필드에 저장되며 다음과 같이 검색할 수 있습니다:

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    `ComposedFunction`은 최소한 Julia 1.6이 필요합니다. 이전 버전에서는 `∘`가 익명 함수를 반환합니다.


자세한 내용은 [`∘`](@ref)를 참조하세요.
