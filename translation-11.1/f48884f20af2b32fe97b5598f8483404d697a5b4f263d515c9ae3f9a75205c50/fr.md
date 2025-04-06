```
print([io::IO = stdout,] data::Vector, lidict::LineInfoDict; kwargs...)
```

Imprime les résultats de profilage dans `io`. Cette variante est utilisée pour examiner les résultats exportés par un appel précédent à [`retrieve`](@ref). Fournissez le vecteur `data` des backtraces et un dictionnaire `lidict` des informations de ligne.

Voir `Profile.print([io], data)` pour une explication des arguments de mot-clé valides.
