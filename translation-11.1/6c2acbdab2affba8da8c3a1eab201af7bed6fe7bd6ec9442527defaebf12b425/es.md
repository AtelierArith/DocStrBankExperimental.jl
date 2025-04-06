```
isless(x, y)
```

Prueba si `x` es menor que `y`, de acuerdo con un orden total fijo (definido junto con [`isequal`](@ref)). `isless` no está definido para pares `(x, y)` de todos los tipos. Sin embargo, si está definido, se espera que satisfaga lo siguiente:

  * Si `isless(x, y)` está definido, entonces también lo están `isless(y, x)` y `isequal(x, y)`, y exactamente uno de esos tres devuelve `true`.
  * La relación definida por `isless` es transitiva, es decir, `isless(x, y) && isless(y, z)` implica `isless(x, z)`.

Los valores que normalmente no tienen orden, como `NaN`, se ordenan después de los valores regulares. Los valores [`missing`](@ref) se ordenan al final.

Esta es la comparación predeterminada utilizada por [`sort!`](@ref).

# Implementación

Los tipos no numéricos con un orden total deben implementar esta función. Los tipos numéricos solo necesitan implementarla si tienen valores especiales como `NaN`. Los tipos con un orden parcial deben implementar [`<`](@ref). Consulta la documentación sobre [Ordenamientos Alternativos](@ref) para saber cómo definir métodos de ordenamiento alternativos que se pueden utilizar en funciones de ordenamiento y relacionadas.

# Ejemplos

```jldoctest
julia> isless(1, 3)
true

julia> isless("Red", "Blue")
false
```
