```
@nospecialize
```

함수 인수 이름에 적용되면, 컴파일러에게 해당 인수의 다양한 유형에 대해 메서드 구현이 특수화되지 않고, 대신 해당 인수에 대해 선언된 유형을 사용해야 함을 힌트합니다. 이는 형식 인수 목록 내의 인수나 함수 본문 내에서 적용될 수 있습니다. 인수에 적용될 때, 매크로는 전체 인수 표현을 감싸야 하며, 예를 들어 `@nospecialize(x::Real)` 또는 `@nospecialize(i::Integer...)`와 같이 인수 이름만 감싸는 것이 아니라 전체를 감싸야 합니다. 함수 본문에서 사용될 때, 매크로는 문장 위치에 있어야 하며, 어떤 코드보다 먼저 나타나야 합니다.

인수 없이 사용될 경우, 이는 부모 범위의 모든 인수에 적용됩니다. 로컬 범위에서는 이는 포함된 함수의 모든 인수를 의미합니다. 글로벌(최상위) 범위에서는 이는 현재 모듈에서 이후에 정의된 모든 메서드를 의미합니다.

특수화는 [`@specialize`](@ref)를 사용하여 기본값으로 재설정할 수 있습니다.

```julia
function example_function(@nospecialize x)
    ...
end

function example_function(x, @nospecialize(y = 1))
    ...
end

function example_function(x, y, z)
    @nospecialize x y
    ...
end

@nospecialize
f(y) = [x for x in y]
@specialize
```

!!! note
    `@nospecialize`는 코드 생성에 영향을 미치지만 추론에는 영향을 미치지 않습니다: 이는 결과적인 네이티브 코드의 다양성을 제한하지만, 유형 추론에 대한 제한(표준 제한을 넘어서는)은 부과하지 않습니다. [`Base.@nospecializeinfer`](@ref)와 함께 `@nospecialize`를 사용하여 추가로 추론을 억제할 수 있습니다.


# 예제

```julia
julia> f(A::AbstractArray) = g(A)
f (generic function with 1 method)

julia> @noinline g(@nospecialize(A::AbstractArray)) = A[1]
g (generic function with 1 method)

julia> @code_typed f([1.0])
CodeInfo(
1 ─ %1 = invoke Main.g(_2::AbstractArray)::Float64
└──      return %1
) => Float64
```

여기서 `@nospecialize` 주석은 다음과 동등한 결과를 생성합니다.

```julia
f(A::AbstractArray) = invoke(g, Tuple{AbstractArray}, A)
```

이는 `g`에 대해 하나의 네이티브 코드 버전만 생성되도록 보장하며, 이는 모든 `AbstractArray`에 대해 일반적입니다. 그러나 특정 반환 유형은 여전히 `g`와 `f` 모두에 대해 추론되며, 이는 여전히 `f`와 `g`의 호출자를 최적화하는 데 사용됩니다.
