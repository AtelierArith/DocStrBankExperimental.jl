```
Slices{P,SM,AX,S,N} <: AbstractSlices{S,N}
```

지정된 차원에서 부모 배열로의 슬라이스를 나타내는 `AbstractArray`로, 다른 차원에서 모든 데이터를 선택하는 뷰를 반환합니다.

이들은 일반적으로 [`eachslice`](@ref), [`eachcol`](@ref) 또는 [`eachrow`](@ref)로 구성되어야 합니다.

[`parent(s::Slices)`](@ref)는 부모 배열을 반환합니다.
