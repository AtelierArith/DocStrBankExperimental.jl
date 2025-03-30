```
in!(x, s::AbstractSet) -> Bool
```

`s`에 `x`가 있으면 `true`를 반환합니다. 그렇지 않으면 `x`를 `s`에 추가하고 `false`를 반환합니다. 이는 `in(x, s) ? true : (push!(s, x); false)`와 동등하지만, 더 효율적인 구현이 있을 수 있습니다.

참고: [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    이 함수는 최소 1.11이 필요합니다.


# 예제

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} with 4 elements:
  4
  2
  3
  1
```
