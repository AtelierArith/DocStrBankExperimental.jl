```
isequal(x, y) -> Bool
```

Similar a [`==`](@ref), excepto por el tratamiento de números de punto flotante y de valores faltantes. `isequal` trata todos los valores `NaN` de punto flotante como iguales entre sí, trata `-0.0` como desigual a `0.0`, y [`missing`](@ref) como igual a `missing`. Siempre devuelve un valor `Bool`.

`isequal` es una relación de equivalencia: es reflexiva (`===` implica `isequal`), simétrica (`isequal(a, b)` implica `isequal(b, a)`) y transitiva (`isequal(a, b)` y `isequal(b, c)` implica `isequal(a, c)`).

# Implementación

La implementación predeterminada de `isequal` llama a `==`, por lo que un tipo que no involucra valores de punto flotante generalmente solo necesita definir `==`.

`isequal` es la función de comparación utilizada por tablas hash (`Dict`). `isequal(x,y)` debe implicar que `hash(x) == hash(y)`.

Esto significa que los tipos para los cuales existe un método personalizado `==` o `isequal` deben implementar un método correspondiente [`hash`](@ref) (y viceversa). Las colecciones generalmente implementan `isequal` llamando a `isequal` recursivamente en todos los contenidos.

Además, `isequal` está vinculado con [`isless`](@ref), y trabajan juntos para definir un orden total fijo, donde exactamente uno de `isequal(x, y)`, `isless(x, y)`, o `isless(y, x)` debe ser `true` (y los otros dos `false`).

Los tipos escalares generalmente no necesitan implementar `isequal` por separado de `==`, a menos que representen números de punto flotante que sean susceptibles a una implementación más eficiente que la proporcionada como una alternativa genérica (basada en `isnan`, `signbit`, y `==`).

# Ejemplos

```jldoctest
julia> isequal([1., NaN], [1., NaN])
true

julia> [1., NaN] == [1., NaN]
false

julia> 0.0 == -0.0
true

julia> isequal(0.0, -0.0)
false

julia> missing == missing
missing

julia> isequal(missing, missing)
true
```
