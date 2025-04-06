```
public
```

`public` est utilisé dans les modules pour indiquer à Julia quels noms font partie de l'API publique du module. Par exemple : `public foo` indique que le nom `foo` est public, sans le rendre disponible lors de [`using`](@ref) du module. Voir la [section du manuel sur les modules](@ref modules) pour plus de détails.

!!! compat "Julia 1.11"
    Le mot-clé public a été ajouté dans Julia 1.11. Avant cela, la notion de publicité était moins explicite.

