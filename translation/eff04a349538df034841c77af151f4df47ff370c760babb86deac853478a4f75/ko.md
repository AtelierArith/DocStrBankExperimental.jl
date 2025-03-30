```
givens(A::AbstractArray, i1::Integer, i2::Integer, j::Integer) -> (G::Givens, r)
```

Givens 회전 `G`와 스칼라 `r`을 계산합니다. 이때 곱셈의 결과가

```
B = G*A
```

다음과 같은 속성을 가집니다.

```
B[i1,j] = r
B[i2,j] = 0
```

자세한 내용은 [`LinearAlgebra.Givens`](@ref)를 참조하세요. ```
