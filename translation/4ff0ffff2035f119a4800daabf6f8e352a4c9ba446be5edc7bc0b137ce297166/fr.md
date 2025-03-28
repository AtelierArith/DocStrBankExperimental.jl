```
estate::EscapeState
```

Lattice étendu qui associe des arguments et des valeurs SSA à des informations d'évasion représentées sous la forme de [`EscapeInfo`](@ref). Les informations d'évasion imposées sur l'élément IR SSA `x` peuvent être récupérées par `estate[x]`.
