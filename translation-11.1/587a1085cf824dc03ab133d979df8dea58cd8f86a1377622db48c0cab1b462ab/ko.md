```
SparseMatrixCSC{Tv,Ti<:Integer} <: AbstractSparseMatrixCSC{Tv,Ti}
```

희소 행렬을 [압축 희소 열](@ref man-csc) 형식으로 저장하기 위한 행렬 유형입니다. SparseMatrixCSC를 구성하는 표준 방법은 [`sparse`](@ref) 함수를 사용하는 것입니다. 또한 [`spzeros`](@ref), [`spdiagm`](@ref) 및 [`sprand`](@ref)를 참조하십시오.
