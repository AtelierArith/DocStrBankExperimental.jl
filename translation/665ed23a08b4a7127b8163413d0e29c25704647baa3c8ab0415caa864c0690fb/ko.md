```
merge!(d::AbstractDict, others::AbstractDict...)
```

다른 컬렉션의 쌍으로 컬렉션을 업데이트합니다. [`merge`](@ref)도 참조하십시오.

# 예제

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> merge!(d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 4
```
