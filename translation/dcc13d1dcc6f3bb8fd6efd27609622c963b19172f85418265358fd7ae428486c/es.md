```
<<(B::BitVector, n) -> BitVector
```

Operador de desplazamiento de bits a la izquierda, `B << n`. Para `n >= 0`, el resultado es `B` con elementos desplazados `n` posiciones hacia atrás, llenando con valores `false`. Si `n < 0`, los elementos se desplazan hacia adelante. Equivalente a `B >> -n`.

# Ejemplos

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B << 1
5-element BitVector:
 0
 1
 0
 0
 0

julia> B << -1
5-element BitVector:
 0
 1
 0
 1
 0
```
