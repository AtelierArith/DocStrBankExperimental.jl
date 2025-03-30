```
mutable struct
```

`mutable struct`는 [`struct`](@ref)와 유사하지만, 추가로 생성 후 타입의 필드를 설정할 수 있습니다.

mutable struct의 개별 필드는 `const`로 표시하여 불변으로 만들 수 있습니다:

```julia
mutable struct Baz
    a::Int
    const b::Float64
end
```

!!! compat "Julia 1.8"
    mutable struct의 필드에 대한 `const` 키워드는 최소한 Julia 1.8이 필요합니다.


자세한 내용은 [Composite Types](@ref) 매뉴얼 섹션을 참조하세요.
