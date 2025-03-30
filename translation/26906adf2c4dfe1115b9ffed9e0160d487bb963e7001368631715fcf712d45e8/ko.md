```
AbstractRange{T} <: AbstractVector{T}
```

타입 `T`의 요소를 가진 선형 범위에 대한 슈퍼타입입니다. [`UnitRange`](@ref), [`LinRange`](@ref) 및 기타 유형은 이의 서브타입입니다.

모든 서브타입은 [`step`](@ref)를 정의해야 합니다. 따라서 [`LogRange`](@ref Base.LogRange)는 `AbstractRange`의 서브타입이 아닙니다.
