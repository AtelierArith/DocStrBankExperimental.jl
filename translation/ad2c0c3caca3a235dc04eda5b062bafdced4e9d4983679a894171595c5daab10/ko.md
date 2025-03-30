```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

제자리에서 버전 [`shuffle`](@ref): 선택적으로 난수 생성기 `rng`를 제공하여 `v`를 제자리에서 무작위로 섞습니다.

# 예제

```jldoctest
julia> shuffle!(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
