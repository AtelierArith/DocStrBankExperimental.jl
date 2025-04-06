```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

다른 컬렉션의 쌍으로 컬렉션을 업데이트합니다. 동일한 키를 가진 값은 조합기 함수를 사용하여 결합됩니다. 커리된 형태인 `mergewith!(combine)`는 함수 `(args...) -> mergewith!(combine, args...)`를 반환합니다.

메서드 `merge!(combine::Union{Function,Type}, args...)`는 `mergewith!(combine, args...)`의 별칭으로 여전히 사용 가능하여 이전 버전과의 호환성을 유지합니다.

!!! compat "Julia 1.5"
    `mergewith!`는 Julia 1.5 이상이 필요합니다.


# 예제

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 0
  1 => 4
```
