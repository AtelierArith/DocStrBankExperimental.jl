```
nor(x, y)
⊽(x, y)
```

NOR a nivel de bits (no o) de `x` y `y`. Implementa [lógica de tres valores](https://en.wikipedia.org/wiki/Three-valued_logic), devolviendo [`missing`](@ref) si uno de los argumentos es `missing` y el otro no es `true`.

La operación infija `a ⊽ b` es un sinónimo de `nor(a,b)`, y `⊽` se puede escribir completando con tabulador `\nor` o `\barvee` en el REPL de Julia.

# Ejemplos

```jldoctest
julia> nor(true, false)
false

julia> nor(true, true)
false

julia> nor(true, missing)
false

julia> false ⊽ false
true

julia> false ⊽ missing
missing

julia> [true; true; false] .⊽ [true; false; false]
3-element BitVector:
 0
 0
 1
```
