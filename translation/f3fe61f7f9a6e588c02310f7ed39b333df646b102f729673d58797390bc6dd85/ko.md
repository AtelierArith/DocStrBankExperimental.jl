```
f ∘ g
```

함수 합성: 즉, `(f ∘ g)(args...; kwargs...)`는 `f(g(args...; kwargs...))`를 의미합니다. `∘` 기호는 Julia REPL(및 적절히 구성된 대부분의 편집기)에서 `\circ<tab>`를 입력하여 입력할 수 있습니다.

함수 합성은 접두사 형식에서도 작동합니다: `∘(f, g)`는 `f ∘ g`와 동일합니다. 접두사 형식은 여러 함수의 합성을 지원합니다: `∘(f, g, h) = f ∘ g ∘ h` 및 iterable 함수 모음을 합성하기 위한 `∘(fs...)`를 지원합니다. `∘`의 마지막 인수는 먼저 실행됩니다.

!!! compat "Julia 1.4"
    여러 함수 합성을 위해서는 최소한 Julia 1.4가 필요합니다.


!!! compat "Julia 1.5"
    하나의 함수 합성 ∘(f)에는 최소한 Julia 1.5가 필요합니다.


!!! compat "Julia 1.7"
    키워드 인수를 사용하려면 최소한 Julia 1.7이 필요합니다.


# 예제

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)
 'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
 'C': ASCII/Unicode U+0043 (category Lu: Letter, uppercase)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

자세한 내용은 [`ComposedFunction`](@ref), [`!f::Function`](@ref)를 참조하세요.
