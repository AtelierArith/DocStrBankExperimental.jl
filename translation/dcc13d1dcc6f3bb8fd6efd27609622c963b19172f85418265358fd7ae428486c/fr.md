```
<<(B::BitVector, n) -> BitVector
```

Opérateur de décalage de bits à gauche, `B << n`. Pour `n >= 0`, le résultat est `B` avec des éléments décalés de `n` positions vers l'arrière, remplis de valeurs `false`. Si `n < 0`, les éléments sont décalés vers l'avant. Équivalent à `B >> -n`.

# Exemples

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
