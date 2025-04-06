```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

`A`를 양방향으로 치환하여 결과 `PAQ` (`A[p,q]`)를 `X`에 저장합니다. 선택적 인수 `C`가 있는 경우 중간 결과 `(AQ)^T` (`transpose(A[:,q])`)를 저장합니다. `X`, `A`, 그리고, 만약 존재한다면 `C`가 서로 별개이어야 합니다; 결과 `PAQ`를 `A`에 다시 저장하려면 `X` 없이 다음 방법을 사용하십시오:

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

`X`의 차원은 `A`의 차원과 일치해야 합니다 (`size(X, 1) == size(A, 1)` 및 `size(X, 2) == size(A, 2)`), 그리고 `X`는 `A`의 모든 할당된 항목을 수용할 수 있는 충분한 저장 공간을 가져야 합니다 (`length(rowvals(X)) >= nnz(A)` 및 `length(nonzeros(X)) >= nnz(A)`). 열 치환 `q`의 길이는 `A`의 열 수와 일치해야 합니다 (`length(q) == size(A, 2)`). 행 치환 `p`의 길이는 `A`의 행 수와 일치해야 합니다 (`length(p) == size(A, 1)`).

`C`의 차원은 `transpose(A)`의 차원과 일치해야 합니다 (`size(C, 1) == size(A, 2)` 및 `size(C, 2) == size(A, 1)`), 그리고 `C`는 `A`의 모든 할당된 항목을 수용할 수 있는 충분한 저장 공간을 가져야 합니다 (`length(rowvals(C)) >= nnz(A)` 및 `length(nonzeros(C)) >= nnz(A)`).

추가적인 (알고리즘적) 정보와 인수 검사를 생략한 이러한 메서드의 버전은 (내보내지 않은) 부모 메서드 `unchecked_noalias_permute!` 및 `unchecked_aliasing_permute!`를 참조하십시오.

또한 [`permute`](@ref)를 참조하십시오.
