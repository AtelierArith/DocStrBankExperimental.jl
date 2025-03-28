```
widen(x)
```

Si `x` est un type, retourne un type "plus grand", défini de sorte que les opérations arithmétiques `+` et `-` ne soient pas garanties de débordement ni de perte de précision pour toute combinaison de valeurs que le type `x` peut contenir.

Pour les types d'entiers à taille fixe inférieurs à 128 bits, `widen` retournera un type avec le double du nombre de bits.

Si `x` est une valeur, elle est convertie en `widen(typeof(x))`.

# Exemples

```jldoctest
julia> widen(Int32)
Int64

julia> widen(1.5f0)
1.5
```
