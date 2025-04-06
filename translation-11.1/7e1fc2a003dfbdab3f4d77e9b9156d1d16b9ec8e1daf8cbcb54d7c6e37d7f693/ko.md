```
givens(f::T, g::T, i1::Integer, i2::Integer) where {T} -> (G::Givens, r::T)
```

주어진 `f`와 `g`에 대해 Givens 회전 `G`와 스칼라 `r`을 계산합니다. 여기서 `x` 벡터는 다음과 같습니다.

```
x[i1] = f
x[i2] = g
```

곱셈의 결과는 다음과 같습니다.

```
y = G*x
```

이때 다음과 같은 속성을 가집니다.

```
y[i1] = r
y[i2] = 0
```

자세한 내용은 [`LinearAlgebra.Givens`](@ref)를 참조하세요.
