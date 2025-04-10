```
QR <: Factorization
```

QR 행렬 분해는 일반적으로 [`qr`](@ref)에서 얻은 압축 형식으로 저장됩니다. 만약 $A$가 `m`×`n` 행렬이라면

$$
A = Q R
$$

여기서 $Q$는 직교/유니타리 행렬이고 $R$은 상삼각 행렬입니다. 행렬 $Q$는 Householder 반사기 $v_i$와 계수 $\tau_i$의 시퀀스로 저장됩니다:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

분해를 반복하면 구성 요소 `Q`와 `R`이 생성됩니다.

객체에는 두 개의 필드가 있습니다:

  * `factors`는 `m`×`n` 행렬입니다.

      * 상삼각 부분은 $R$의 요소를 포함하며, 즉 `R = triu(F.factors)`는 `QR` 객체 `F`에 대해 성립합니다.
      * 하대각선 부분은 압축 형식으로 저장된 반사기 $v_i$를 포함하며, 여기서 $v_i$는 행렬 `V = I + tril(F.factors, -1)`의 $i$번째 열입니다.
  * `τ`는 길이가 `min(m,n)`인 벡터로, 계수 $au_i$를 포함합니다.
