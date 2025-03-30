```
svd(A; full::Bool = false, alg::Algorithm = default_svd_alg(A)) -> SVD
```

행렬 `A`의 특이값 분해(SVD)를 계산하고 `SVD` 객체를 반환합니다.

`U`, `S`, `V` 및 `Vt`는 `F`의 분해에서 `F.U`, `F.S`, `F.V` 및 `F.Vt`를 사용하여 얻을 수 있으며, 이때 `A = U * Diagonal(S) * Vt`입니다. 알고리즘은 `Vt`를 생성하므로 `Vt`를 추출하는 것이 `V`보다 더 효율적입니다. `S`의 특이값은 내림차순으로 정렬되어 있습니다.

분해를 반복하면 구성 요소 `U`, `S` 및 `V`를 생성합니다.

`full = false`(기본값)인 경우 "얇은" SVD가 반환됩니다. $M \times N$ 행렬 `A`의 경우, 전체 분해에서 `U`는 $M \times M$이고 `V`는 $N \times N$이며, 얇은 분해에서 `U`는 $M \times K$이고 `V`는 $N \times K$입니다. 여기서 $K = \min(M,N)$는 특이값의 수입니다.

`alg = DivideAndConquer()`인 경우 분할 정복 알고리즘을 사용하여 SVD를 계산합니다. 또 다른 옵션은 `alg = QRIteration()`으로, 일반적으로 더 느리지만 더 정확합니다.

!!! compat "Julia 1.3"
    `alg` 키워드 인수는 Julia 1.3 이상이 필요합니다.


# 예제

```jldoctest
julia> A = rand(4,3);

julia> F = svd(A); # 분해 객체 저장

julia> A ≈ F.U * Diagonal(F.S) * F.Vt
true

julia> U, S, V = F; # 반복을 통한 구조 분해

julia> A ≈ U * Diagonal(S) * V'
true

julia> Uonly, = svd(A); # U만 저장

julia> Uonly == U
true
```
