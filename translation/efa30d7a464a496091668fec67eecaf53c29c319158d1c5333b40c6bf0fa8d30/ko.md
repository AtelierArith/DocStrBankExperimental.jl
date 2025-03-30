```
sparse(I, J, V,[ m, n, combine])
```

`S`라는 희소 행렬을 `m x n` 크기로 생성하여 `S[I[k], J[k]] = V[k]`가 되도록 합니다. `combine` 함수는 중복을 결합하는 데 사용됩니다. `m`과 `n`이 지정되지 않으면 각각 `maximum(I)`와 `maximum(J)`로 설정됩니다. `combine` 함수가 제공되지 않으면, `combine`은 기본적으로 `+`로 설정되지만, `V`의 요소가 Boolean인 경우 `combine`은 기본적으로 `|`로 설정됩니다. `I`의 모든 요소는 `1 <= I[k] <= m`을 만족해야 하며, `J`의 모든 요소는 `1 <= J[k] <= n`을 만족해야 합니다. (`I`, `J`, `V`)의 수치적 0은 구조적 비제로로 유지됩니다; 수치적 0을 제거하려면 [`dropzeros!`](@ref)를 사용하십시오.

추가 문서 및 전문가 드라이버는 `SparseArrays.sparse!`를 참조하십시오.

# 예제

```jldoctest
julia> Is = [1; 2; 3];

julia> Js = [1; 2; 3];

julia> Vs = [1; 2; 3];

julia> sparse(Is, Js, Vs)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 1  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  3
```
