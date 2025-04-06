```
merge(d::AbstractDict, others::AbstractDict...)
```

주어진 컬렉션에서 병합된 컬렉션을 생성합니다. 필요한 경우, 결과 컬렉션의 유형은 병합된 컬렉션의 유형을 수용하도록 승격됩니다. 동일한 키가 다른 컬렉션에 존재하는 경우, 해당 키의 값은 나열된 마지막 컬렉션에서 가진 값이 됩니다. 동일한 키를 가진 값에 대한 사용자 정의 처리를 위해 [`mergewith`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} with 2 entries:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} with 2 entries:
  "bar" => 4711
  "baz" => 17

julia> merge(a, b)
Dict{String, Float64} with 3 entries:
  "bar" => 4711.0
  "baz" => 17.0
  "foo" => 0.0

julia> merge(b, a)
Dict{String, Float64} with 3 entries:
  "bar" => 42.0
  "baz" => 17.0
  "foo" => 0.0
```
