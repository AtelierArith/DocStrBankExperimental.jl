```
!f::Function
```

프레디케이트 함수 부정: `!`의 인수가 함수일 때, `f`의 불리언 부정을 계산하는 합성 함수를 반환합니다.

자세한 내용은 [`∘`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! compat "Julia 1.9"
    Julia 1.9부터 `!f`는 익명 함수 대신 [`ComposedFunction`](@ref)를 반환합니다.

