```
names(x::Module; all::Bool = false, imported::Bool = false)
```

Obtenez un vecteur des noms publics d'un `Module`, en excluant les noms obsolètes. Si `all` est vrai, la liste inclut également les noms non publics définis dans le module, les noms obsolètes et les noms générés par le compilateur. Si `imported` est vrai, alors les noms explicitement importés d'autres modules sont également inclus. Les noms sont retournés dans un ordre trié.

En tant que cas particulier, tous les noms définis dans `Main` sont considérés comme "publics", car il n'est pas idiomatique de marquer explicitement les noms de `Main` comme publics.

!!! note
    `sym ∈ names(SomeModule)` ne signifie *pas* `isdefined(SomeModule, sym)`. `names` renverra des symboles marqués avec `public` ou `export`, même s'ils ne sont pas définis dans le module.


Voir aussi : [`Base.isexported`](@ref), [`Base.ispublic`](@ref), [`Base.@locals`](@ref), [`@__MODULE__`](@ref).
