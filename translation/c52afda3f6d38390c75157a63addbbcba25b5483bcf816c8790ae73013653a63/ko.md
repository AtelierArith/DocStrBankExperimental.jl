```
유사한(A::AbstractSparseMatrixCSC{Tv,Ti}, [::Type{TvNew}, ::Type{TiNew}, m::Integer, n::Integer]) where {Tv,Ti}
```

주어진 요소 유형, 인덱스 유형 및 크기를 기반으로 주어진 소스 `SparseMatrixCSC`로 초기화되지 않은 가변 배열을 생성합니다. 새로운 희소 행렬은 원래 희소 행렬의 구조를 유지하지만 출력 행렬의 차원이 다를 경우를 제외합니다.

출력 행렬은 입력과 동일한 위치에 0이 있지만 비영(非零) 위치에는 초기화되지 않은 값이 있습니다.
