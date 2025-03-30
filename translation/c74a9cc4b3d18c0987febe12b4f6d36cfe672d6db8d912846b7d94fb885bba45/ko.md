```
SymTridiagonal(dv::V, ev::V) where V <: AbstractVector
```

대각선(`dv`)과 첫 번째 하위/상위 대각선(`ev`)으로부터 대칭 삼대각 행렬을 구성합니다. 결과는 `SymTridiagonal` 유형이며, 효율적인 특수 고유값 솔버를 제공하지만 [`convert(Array, _)`](@ref) (또는 짧게 `Array(_)`)를 사용하여 일반 행렬로 변환할 수 있습니다.

`SymTridiagonal` 블록 행렬의 경우, `dv`의 요소는 대칭화됩니다. 인수 `ev`는 상위 대각선으로 해석됩니다. 하위 대각선의 블록은 해당 상위 대각선 블록의 (구현된) 전치입니다.

# 예제

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
