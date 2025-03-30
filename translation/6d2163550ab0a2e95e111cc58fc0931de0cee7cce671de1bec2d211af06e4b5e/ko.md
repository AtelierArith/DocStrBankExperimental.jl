```
Vararg{T,N}
```

튜플 타입 [`Tuple`](@ref)의 마지막 매개변수는 특별한 값 `Vararg`일 수 있으며, 이는 임의의 수의 후행 요소를 나타냅니다. `Vararg{T,N}`은 정확히 `N`개의 `T` 타입 요소에 해당합니다. 마지막으로 `Vararg{T}`는 0개 이상의 `T` 타입 요소에 해당합니다. `Vararg` 튜플 타입은 가변 인수 메서드에서 허용되는 인수를 나타내는 데 사용됩니다(매뉴얼의 [Varargs Functions](@ref) 섹션 참조).

또한 [`NTuple`](@ref)를 참조하십시오.

# 예제

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
