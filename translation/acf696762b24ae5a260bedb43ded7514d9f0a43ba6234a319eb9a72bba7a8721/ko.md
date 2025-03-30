```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

주어진 컬렉션에서 병합된 컬렉션을 구성합니다. 필요한 경우, 결과 컬렉션의 유형은 병합된 컬렉션의 유형을 수용하도록 승격됩니다. 동일한 키를 가진 값은 조합기 함수를 사용하여 결합됩니다. 커리된 형태 `mergewith(combine)`는 함수 `(args...) -> mergewith(combine, args...)`를 반환합니다.

메서드 `merge(combine::Union{Function,Type}, args...)`는 `mergewith(combine, args...)`의 별칭으로 여전히 사용 가능하여 이전 호환성을 유지합니다.

!!! compat "Julia 1.5"
    `mergewith`는 Julia 1.5 이상이 필요합니다.


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

julia> mergewith(+, a, b)
Dict{String, Float64} with 3 entries:
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
