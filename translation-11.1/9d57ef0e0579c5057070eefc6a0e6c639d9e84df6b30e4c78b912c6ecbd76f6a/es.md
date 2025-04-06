```
OrdinalRange{T, S} <: AbstractRange{T}
```

Supertipo para rangos ordinales con elementos de tipo `T` con espaciado(s) de tipo `S`. Los pasos deben ser siempre múltiplos exactos de [`oneunit`](@ref), y `T` debe ser un tipo "discreto", que no puede tener valores menores que `oneunit`. Por ejemplo, los tipos `Integer` o `Date` calificarían, mientras que `Float64` no lo haría (ya que este tipo puede representar valores menores que `oneunit(Float64)`). [`UnitRange`](@ref), [`StepRange`](@ref), y otros tipos son subtipos de esto.
