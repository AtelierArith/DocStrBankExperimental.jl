```
quote
```

`quote` crée plusieurs objets d'expression dans un bloc sans utiliser le constructeur explicite [`Expr`](@ref). Par exemple :

```julia
ex = quote
    x = 1
    y = 2
    x + y
end
```

Contrairement aux autres moyens de citation, `:( ... )`, cette forme introduit des éléments `QuoteNode` dans l'arbre d'expression, qui doivent être pris en compte lors de la manipulation directe de l'arbre. Pour d'autres usages, `:( ... )` et les blocs `quote .. end` sont traités de manière identique.
