```
precompile(f, argtypes::Tuple{Vararg{Any}}, m::Method)
```

Précompiler une méthode spécifique pour les types d'arguments donnés. Cela peut être utilisé pour précompiler une méthode différente de celle qui serait normalement choisie par le dispatch, imitant ainsi `invoke`.
