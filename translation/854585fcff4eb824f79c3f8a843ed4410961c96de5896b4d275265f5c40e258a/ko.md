```
(I::UniformScaling)(n::Integer)
```

`UniformScaling`에서 `Diagonal` 행렬을 생성합니다.

!!! compat "Julia 1.2"
    이 메서드는 Julia 1.2부터 사용할 수 있습니다.


# 예제

```jldoctest
julia> I(3)
3×3 Diagonal{Bool, Vector{Bool}}:
 1  ⋅  ⋅
 ⋅  1  ⋅
 ⋅  ⋅  1

julia> (0.7*I)(3)
3×3 Diagonal{Float64, Vector{Float64}}:
 0.7   ⋅    ⋅
  ⋅   0.7   ⋅
  ⋅    ⋅   0.7
```
