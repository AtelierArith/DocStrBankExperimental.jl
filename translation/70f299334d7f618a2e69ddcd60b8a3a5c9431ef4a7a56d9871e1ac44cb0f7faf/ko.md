```
Union{Types...}
```

`Union` 타입은 그 인수 타입의 모든 인스턴스를 포함하는 추상 타입입니다. 이는 `T <: Union{T,S}` 및 `S <: Union{T,S}`를 의미합니다.

다른 추상 타입과 마찬가지로, 모든 인수가 비추상적일지라도 인스턴스화할 수 없습니다.

# 예제

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString # Int의 인스턴스는 유니온에 포함됩니다.
true

julia> "Hello!" isa IntOrString # String도 포함됩니다.
true

julia> 1.0 isa IntOrString # Float64는 Int도 AbstractString도 아니기 때문에 포함되지 않습니다.
false
```

# 추가 도움말

대부분의 다른 매개변수 타입과 달리, 유니온은 그 매개변수에 대해 공변적입니다. 예를 들어, `Union{Real, String}`은 `Union{Number, AbstractString}`의 하위 타입입니다.

빈 유니온 [`Union{}`](@ref)는 Julia의 바닥 타입입니다.
