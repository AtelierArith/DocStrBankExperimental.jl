```
xor(x, y)
⊻(x, y)
```

O exclusivo a nivel de bits de `x` e `y`. Implementa [lógica de tres valores](https://es.wikipedia.org/wiki/L%C3%B3gica_de_tres_valores), devolviendo [`missing`](@ref) si uno de los argumentos es `missing`.

La operación infija `a ⊻ b` es un sinónimo de `xor(a,b)`, y `⊻` se puede escribir completando con tabulador `\xor` o `\veebar` en el REPL de Julia.

# Ejemplos

```jldoctest
julia> xor(true, false)
true

julia> xor(true, true)
false

julia> xor(true, missing)
missing

julia> false ⊻ false
false

julia> [true; true; false] .⊻ [true; false; false]
3-element BitVector:
 0
 1
 0
```
