```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

전달된 집합의 [`union`](@ref)를 구성하고 결과로 `s`를 덮어씁니다. 배열의 순서를 유지합니다.

!!! 경고     변형된 인수 중 하나가 다른 인수와 메모리를 공유할 경우 동작이 예기치 않게 될 수 있습니다.

# 예제

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} with 5 elements:
  5
  4
  7
  3
  1
```
