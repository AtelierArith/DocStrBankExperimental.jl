```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

열을 재배열하고 `A`를 전치하며, 동시에 `f`를 `A`의 각 항목에 적용하고 결과 `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`)를 `X`에 저장합니다.

`X`의 요소 유형 `Tv`는 `f(::TvA)`와 일치해야 하며, 여기서 `TvA`는 `A`의 요소 유형입니다. `X`의 차원은 `transpose(A)`의 차원과 일치해야 하며 (`size(X, 1) == size(A, 2)` 및 `size(X, 2) == size(A, 1)`), `X`는 `A`의 모든 할당된 항목을 수용할 수 있는 충분한 저장 공간을 가져야 합니다 (`length(rowvals(X)) >= nnz(A)` 및 `length(nonzeros(X)) >= nnz(A)`). 열 재배열 `q`의 길이는 `A`의 열 수와 일치해야 합니다 (`length(q) == size(A, 2)`).

이 메서드는 [`SparseMatrixCSC`](@ref)에서 전치 및 재배열 작업을 수행하는 여러 메서드의 부모입니다. 이 메서드는 인수 검사를 수행하지 않으므로, 직접 사용하기보다는 더 안전한 자식 메서드 (`[c]transpose[!]`, `permute[!]`)를 사용하는 것이 좋습니다.

이 메서드는 F. Gustavson의 "희소 행렬을 위한 두 가지 빠른 알고리즘: 곱셈 및 재배열된 전치," ACM TOMS 4(3), 250-269 (1978)에서 설명된 `HALFPERM` 알고리즘을 구현합니다. 이 알고리즘은 `O(size(A, 1), size(A, 2), nnz(A))` 시간에 실행되며, 전달된 것 외에 추가 공간이 필요하지 않습니다.
