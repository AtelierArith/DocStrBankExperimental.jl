```
QRCompactWY <: Factorization
```

QR 행렬 분해는 일반적으로 [`qr`](@ref)에서 얻어진 압축 블록 형식으로 저장됩니다. 만약 $A$가 `m`×`n` 행렬이라면

$$
A = Q R
$$

여기서 $Q$는 직교/유니타리 행렬이고 $R$은 상삼각형입니다. 이는 [`QR`](@ref) 형식과 유사하지만, 직교/유니타리 행렬 $Q$가 *Compact WY* 형식으로 저장됩니다 [^Schreiber1989]. 블록 크기 $n_b$에 대해, 이는 `m`×`n` 하사다리꼴 행렬 $V$와 $b = \lceil \min(m,n) / n_b \rceil$ 개의 크기 $n_b$×$n_b$ 상삼각형 행렬 $T_j$로 구성된 행렬 $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$로 저장됩니다 ($j = 1, ..., b-1$) 및 상하사다리꼴 $n_b$×$\min(m,n) - (b-1) n_b$ 행렬 $T_b'$ ($j=b$)로, 그 상단 정사각형 부분은 $T_b$로 표시되며 다음을 만족합니다.

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

여기서 $v_i$는 $V$의 $i$번째 열, $\tau_i$는 `[diag(T_1); diag(T_2); …; diag(T_b)]`의 $i$번째 요소이며, $(V_1 \; V_2 \; ... \; V_b)$는 $V$의 왼쪽 `m`×`min(m, n)` 블록입니다. [`qr`](@ref)로 구성할 때, 블록 크기는 $n_b = \min(m, n, 36)$로 주어집니다.

분해를 반복하면 구성 요소 `Q`와 `R`이 생성됩니다.

객체에는 두 개의 필드가 있습니다:

  * `factors`, [`QR`](@ref) 유형과 같이, `m`×`n` 행렬입니다.

      * 상삼각형 부분에는 $R$의 요소가 포함되어 있으며, 즉 `R = triu(F.factors)`는 `QR` 객체 `F`에 대해 성립합니다.
      * 하대각선 부분에는 패킹 형식으로 저장된 반사기 $v_i$가 포함되어 있으며, `V = I + tril(F.factors, -1)`입니다.
  * `T`는 위에서 설명한 대로 $n_b$-by-$\min(m,n)$ 행렬입니다. 각 삼각형 행렬 $T_j$의 하대각선 요소는 무시됩니다.

!!! note
    이 형식은 이전의 *WY* 표현 [^Bischof1987]과 혼동해서는 안 됩니다.


[^Bischof1987]: C Bischof and C Van Loan, "The WY representation for products of Householder matrices", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber and C Van Loan, "A storage-efficient WY representation for products of Householder transformations", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
