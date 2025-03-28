```
AbstractIrrational <: Real
```

Tipo de número que representa un valor irracional exacto, que se redondea automáticamente a la precisión correcta en operaciones aritméticas con otras cantidades numéricas.

Los subtipos `MyIrrational <: AbstractIrrational` deben implementar al menos `==(::MyIrrational, ::MyIrrational)`, `hash(x::MyIrrational, h::UInt)`, y `convert(::Type{F}, x::MyIrrational) donde {F <: Union{BigFloat,Float32,Float64}}`.

Si un subtipo se utiliza para representar valores que pueden ser ocasionalmente racionales (por ejemplo, un tipo de raíz cuadrada que representa `√n` para enteros `n` dará un resultado racional cuando `n` es un cuadrado perfecto), entonces también debe implementar `isinteger`, `iszero`, `isone`, y `==` con valores `Real` (ya que todos estos predeterminan a `false` para tipos `AbstractIrrational`), así como definir [`hash`](@ref) para que sea igual al correspondiente `Rational`.
