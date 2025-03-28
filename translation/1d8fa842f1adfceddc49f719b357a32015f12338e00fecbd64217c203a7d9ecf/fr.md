```
Profile.Allocs.print([io::IO = stdout,] [data::AllocResults = fetch()]; kwargs...)
```

Imprime les résultats de profilage dans `io` (par défaut, `stdout`). Si vous ne fournissez pas de vecteur `data`, le tampon interne des backtraces accumulées sera utilisé.

Voir `Profile.print` pour une explication des arguments de mot-clé valides.
