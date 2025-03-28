```
propertynames(x, private=false)
```

Obtenez un tuple ou un vecteur des propriétés (`x.property`) d'un objet `x`. Cela correspond généralement à [`fieldnames(typeof(x))`](@ref), mais les types qui redéfinissent [`getproperty`](@ref) devraient généralement redéfinir `propertynames` également pour obtenir les propriétés d'une instance du type.

`propertynames(x)` peut ne retourner que les noms de propriétés "publiques" qui font partie de l'interface documentée de `x`. Si vous souhaitez qu'il retourne également les noms de propriétés "privées" destinées à un usage interne, passez `true` comme deuxième argument optionnel. La complétion par tabulation dans le REPL sur `x.` n'affiche que les propriétés `private=false`.

Voir aussi : [`hasproperty`](@ref), [`hasfield`](@ref).
