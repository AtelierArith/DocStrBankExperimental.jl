```
Base.@nospecializeinfer function f(args...)
    @nospecialize ...
    ...
end
Base.@nospecializeinfer f(@nospecialize args...) = ...
```

컴파일러에게 `@nospecialize`된 인수의 선언된 유형을 사용하여 `f`를 추론하도록 지시합니다. 이는 추론 중에 컴파일러가 생성하는 특수화의 수를 제한하는 데 사용할 수 있습니다.

# 예제

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline Base.@nospecializeinfer g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Any
└──      return %1
) => Any
```

이 예제에서 `f`는 `A`의 각 특정 유형에 대해 추론되지만, `g`는 선언된 인수 유형 `A::AbstractArray`로 한 번만 추론됩니다. 이는 컴파일러가 그것에 대한 과도한 추론 시간을 보지 않을 가능성이 높다는 것을 의미합니다. `@nospecializeinfer` 없이 `f([1.0])`는 `g`의 반환 유형을 `Float64`로 추론하게 되며, 이는 특수화된 코드 생성을 금지했음에도 불구하고 `g(::Vector{Float64})`에 대해 추론이 실행되었음을 나타냅니다.

!!! compat "Julia 1.10"
    `Base.@nospecializeinfer`를 사용하려면 Julia 버전 1.10이 필요합니다.

