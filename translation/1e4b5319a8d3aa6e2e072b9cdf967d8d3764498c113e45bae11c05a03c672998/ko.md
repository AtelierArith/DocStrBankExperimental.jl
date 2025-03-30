```
Union{}
```

`Union{}`, 빈 [`Union`](@ref) 타입은 값이 없는 타입입니다. 즉, `x`가 어떤 것이든 `isa(x, Union{}) == false`라는 정의 속성을 가집니다. `Base.Bottom`은 그 별칭으로 정의되며 `Union{}`의 타입은 `Core.TypeofBottom`입니다.

# 예제

```jldoctest
julia> isa(nothing, Union{})
false
```
