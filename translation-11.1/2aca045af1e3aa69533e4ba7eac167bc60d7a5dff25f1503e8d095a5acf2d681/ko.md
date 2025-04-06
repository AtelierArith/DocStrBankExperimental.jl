```
middle(a::AbstractArray)
```

배열 `a`의 중간값을 계산합니다. 이는 배열의 극값을 찾고 그 평균을 계산하는 것입니다.

```jldoctest
julia> using Statistics

julia> middle(1:10)
5.5

julia> a = [1,2,3.6,10.9]
4-element Vector{Float64}:
  1.0
  2.0
  3.6
 10.9

julia> middle(a)
5.95
```
