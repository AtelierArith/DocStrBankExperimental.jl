```
condskeel(M, [x, p::Real=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

행렬 `M`의 Skeel 조건 수 $\kappa_S$는 선택적으로 벡터 `x`에 대해 계산되며, 연산자 `p`-노름을 사용합니다. $\left\vert M \right\vert$는 $M$의 (항목별) 절대값 행렬을 나타내며; :\left\vert M \right\vert*{ij} = \left\vert M*{ij} \right\vert. `p`의 유효한 값은 `1`, `2` 및 `Inf` (기본값)입니다.

이 양은 문헌에서 바우어 조건 수, 상대 조건 수 또는 항목별 상대 조건 수로도 알려져 있습니다.
