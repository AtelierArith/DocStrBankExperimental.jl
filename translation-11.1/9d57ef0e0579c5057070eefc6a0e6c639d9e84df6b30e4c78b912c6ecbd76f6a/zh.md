```
OrdinalRange{T, S} <: AbstractRange{T}
```

用于具有类型 `T` 的元素和类型 `S` 的间隔的序数范围的超类型。步长应始终是 [`oneunit`](@ref) 的精确倍数，并且 `T` 应该是“离散”类型，不能有小于 `oneunit` 的值。例如，`Integer` 或 `Date` 类型符合条件，而 `Float64` 则不符合（因为该类型可以表示小于 `oneunit(Float64)` 的值）。[`UnitRange`](@ref)、[`StepRange`](@ref) 和其他类型是此类型的子类型。
