```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> Eigen
```

행렬 `A`의 고유값 분해를 계산하고, 고유값을 `F.values`에, 고유벡터를 행렬 `F.vectors`의 열에 포함하는 [`Eigen`](@ref) 분해 객체 `F`를 반환합니다. (`k`번째 고유벡터는 슬라이스 `F.vectors[:, k]`에서 얻을 수 있습니다.)

분해를 반복하면 구성 요소 `F.values`와 `F.vectors`를 생성합니다.

`Eigen` 객체에 대해 사용할 수 있는 함수는 [`inv`](@ref), [`det`](@ref), 및 [`isposdef`](@ref)입니다.

`vl`은 검색할 고유값의 윈도우의 하한이며, `vu`는 상한입니다.

!!! note
    만약 [`vl`, `vu`]가 `A`의 모든 고유값을 포함하지 않는다면, 반환된 분해는 *잘린* 분해가 됩니다.

