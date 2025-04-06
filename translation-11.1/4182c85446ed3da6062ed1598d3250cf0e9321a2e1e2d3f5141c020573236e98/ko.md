```
IdSet{T}([itr])
IdSet()
```

IdSet{T}()는 `T` 유형의 값에 대해 동등성으로 `===`를 사용하여 집합(see [`Set`](@ref))을 구성합니다.

아래 예제에서 값들은 모두 `isequal`이므로 일반 `Set`에서 덮어씌워집니다. `IdSet`은 `===`로 비교하므로 3개의 서로 다른 값을 보존합니다.

# 예제

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} with 1 element:
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} with 3 elements:
  1.0
  1
  true
```
