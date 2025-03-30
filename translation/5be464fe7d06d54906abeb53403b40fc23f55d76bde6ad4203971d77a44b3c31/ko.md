```
sparse_hvcat(rows::Tuple{Vararg{Int}}, values...)
```

한 번의 호출로 희소 수평 및 수직 연결. 이 함수는 블록 행렬 구문에 대해 호출됩니다. 첫 번째 인수는 각 블록 행에서 연결할 인수의 수를 지정합니다.

!!! compat "Julia 1.8"
    이 메서드는 Julia 1.8에 추가되었습니다. 이는 LinearAlgebra.jl의 특수 "희소" 행렬 유형과의 연결이 SparseArray 인수가 없더라도 자동으로 희소 출력을 생성하는 이전 연결 동작을 모방합니다.

