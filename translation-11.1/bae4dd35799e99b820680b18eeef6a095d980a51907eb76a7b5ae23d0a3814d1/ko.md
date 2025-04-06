```
UnionAll
```

타입 매개변수의 모든 값에 대한 타입의 합집합입니다. `UnionAll`은 일부 매개변수의 값이 알려지지 않은 매개변수 타입을 설명하는 데 사용됩니다. [UnionAll Types](@ref) 섹션을 참조하십시오.

# 예제

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
