```
OrdinalRange{T, S} <: AbstractRange{T}
```

유형 `T`의 요소와 유형 `S`의 간격을 가진 서수 범위의 슈퍼타입입니다. 단계는 항상 [`oneunit`](@ref)의 정확한 배수여야 하며, `T`는 `oneunit`보다 작은 값을 가질 수 없는 "불연속" 유형이어야 합니다. 예를 들어, `Integer` 또는 `Date` 유형은 적합하지만, `Float64`는 적합하지 않습니다(이 유형은 `oneunit(Float64)`보다 작은 값을 나타낼 수 있기 때문입니다). [`UnitRange`](@ref), [`StepRange`](@ref) 및 기타 유형은 이의 하위 유형입니다.
