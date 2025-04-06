```
IdDict([itr])
```

`IdDict{K,V}()`는 [`objectid`](@ref)를 해시로 사용하고 `===`를 동등성으로 사용하여 키의 유형이 `K`이고 값의 유형이 `V`인 해시 테이블을 구성합니다. 추가 도움은 [`Dict`](@ref)를 참조하고, 이의 집합 버전은 [`IdSet`](@ref)를 참조하세요.

아래 예제에서 `Dict` 키는 모두 `isequal`이므로 동일하게 해시되어 덮어씌워집니다. `IdDict`는 객체 ID로 해시하므로 3개의 서로 다른 키를 유지합니다.

# 예제

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
