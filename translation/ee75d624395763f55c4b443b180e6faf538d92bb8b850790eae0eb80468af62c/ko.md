```
hasfield(T::Type, name::Symbol)
```

`T`가 자신의 필드 중 하나로 `name`을 가지고 있는지 여부를 나타내는 불리언을 반환합니다.

자세한 내용은 [`fieldnames`](@ref), [`fieldcount`](@ref), [`hasproperty`](@ref)를 참조하세요.

!!! compat "Julia 1.2"
    이 함수는 최소한 Julia 1.2가 필요합니다.


# 예제

```jldoctest
julia> struct Foo
            bar::Int
       end

julia> hasfield(Foo, :bar)
true

julia> hasfield(Foo, :x)
false
```
