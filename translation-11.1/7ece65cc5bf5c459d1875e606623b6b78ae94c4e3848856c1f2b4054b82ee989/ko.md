```
svd(A, B) -> GeneralizedSVD
```

`A`와 `B`의 일반화된 SVD를 계산하여 `F`라는 `GeneralizedSVD` 분해 객체를 반환합니다. 여기서 `[A;B] = [F.U * F.D1; F.V * F.D2] * F.R0 * F.Q'`입니다.

  * `U`는 M-by-M 직교 행렬입니다.
  * `V`는 P-by-P 직교 행렬입니다.
  * `Q`는 N-by-N 직교 행렬입니다.
  * `D1`은 첫 K 항목에 1이 있는 M-by-(K+L) 대각 행렬입니다.
  * `D2`는 상단 오른쪽 L-by-L 블록이 대각선인 P-by-(K+L) 행렬입니다.
  * `R0`는 가장 오른쪽 (K+L)-by-(K+L) 블록이 비특이 상부 블록 삼각형인 (K+L)-by-N 행렬입니다.

`K+L`은 행렬 `[A; B]`의 유효 수치적 계수입니다.

분해를 반복하면 구성 요소 `U`, `V`, `Q`, `D1`, `D2`, 및 `R0`가 생성됩니다.

일반화된 SVD는 `A`와 `B`의 비교가 필요할 때, 예를 들어 인간과 효모 유전체, 신호와 잡음, 또는 클러스터 간과 클러스터 내의 비교와 같은 응용 프로그램에서 사용됩니다. (논의는 Edelman과 Wang을 참조하십시오: https://arxiv.org/abs/1901.00485)

이것은 `[A; B]`를 `[UC; VS]H`로 분해하며, 여기서 `[UC; VS]`는 `[A; B]`의 열 공간에 대한 자연스러운 직교 기저이고, `H = RQ'`는 `[A;B]`의 행 공간에 대한 자연스러운 비직교 기저입니다. 여기서 상단 행은 `A` 행렬에 가장 밀접하게 귀속되고, 하단 행은 `B` 행렬에 귀속됩니다. 다중 코사인/사인 행렬 `C`와 `S`는 `A`와 `B`의 비율을 측정하는 다중 측정을 제공합니다. `U`와 `V`는 이러한 측정이 이루어지는 방향을 제공합니다.

# 예제

```jldoctest
julia> A = randn(3,2); B=randn(4,2);

julia> F = svd(A, B);

julia> U,V,Q,C,S,R = F;

julia> H = R*Q';

julia> [A; B] ≈ [U*C; V*S]*H
true

julia> [A; B] ≈ [F.U*F.D1; F.V*F.D2]*F.R0*F.Q'
true

julia> Uonly, = svd(A,B);

julia> U == Uonly
true
```
