```
Integer <: Real
```

모든 정수에 대한 추상 슈퍼타입(예: [`Signed`](@ref), [`Unsigned`](@ref), 및 [`Bool`](@ref)).

또한 [`isinteger`](@ref), [`trunc`](@ref), [`div`](@ref)를 참조하십시오.

# 예제

```
julia> 42 isa Integer
true

julia> 1.0 isa Integer
false

julia> isinteger(1.0)
true
```
