```
nand(x, y)
⊼(x, y)
```

Nand a nivel de bits (no y) de `x` e `y`. Implementa [lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores), devolviendo [`missing`](@ref) si uno de los argumentos es `missing`.

La operación infija `a ⊼ b` es un sinónimo de `nand(a,b)`, y `⊼` se puede escribir completando con tabulador `\nand` o `\barwedge` en el REPL de Julia.

# Ejemplos

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
