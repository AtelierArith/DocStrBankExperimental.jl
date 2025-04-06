```
shuffle([rng=default_rng(),] v::AbstractArray)
```

`v`의 무작위로 섞인 복사본을 반환합니다. 선택적 `rng` 인자는 난수 생성기를 지정합니다(자세한 내용은 [난수](@ref) 참조). `v`를 제자리에서 섞으려면 [`shuffle!`](@ref)를 참조하세요. 무작위로 섞인 인덱스를 얻으려면 [`randperm`](@ref)를 참조하세요.

# 예제

```jldoctest
julia> shuffle(Xoshiro(123), Vector(1:10))
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
