```
undocumented_names(mod::Module; private=false)
```

Renvoie un vecteur trié de symboles non documentés dans `module` (c'est-à-dire, sans docstrings). `private=false` (la valeur par défaut) renvoie uniquement les identifiants déclarés avec `public` et/ou `export`, tandis que `private=true` renvoie tous les symboles dans le module (à l'exception des symboles cachés générés par le compilateur commençant par `#`).

Voir aussi : [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
