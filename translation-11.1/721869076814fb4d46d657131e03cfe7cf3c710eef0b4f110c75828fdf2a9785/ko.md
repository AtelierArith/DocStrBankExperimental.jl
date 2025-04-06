```
mul!(C, A, B, α, β) -> C
```

결합된 제자리 행렬-행렬 또는 행렬-벡터 곱셈-덧셈 $A B α + C β$. 결과는 `C`에 저장되며, 이를 덮어씁니다. `C`는 `A` 또는 `B`와 별개이어야 합니다.

!!! compat "Julia 1.3"
    다섯 개 인수를 가진 `mul!`는 최소한 Julia 1.3이 필요합니다.


# 예제

```jldoctest
julia> A = [1.0 2.0; 3.0 4.0]; B = [1.0 1.0; 1.0 1.0]; C = [1.0 2.0; 3.0 4.0];

julia> α, β = 100.0, 10.0;

julia> mul!(C, A, B, α, β) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0

julia> C_original = [1.0 2.0; 3.0 4.0]; # C의 원래 값의 복사본

julia> C == A * B * α + C_original * β
true
```
