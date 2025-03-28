```
@lock l expr
```

Version macro de `lock(f, l::AbstractLock)` mais avec `expr` au lieu de la fonction `f`. Se développe en :

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

C'est similaire à l'utilisation de [`lock`](@ref) avec un bloc `do`, mais évite de créer une fermeture et peut donc améliorer les performances.

!!! compat
    `@lock` a été ajouté dans Julia 1.3 et exporté dans Julia 1.10.

