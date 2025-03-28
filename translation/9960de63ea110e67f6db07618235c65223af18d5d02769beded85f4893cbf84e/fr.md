```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

Définit le type déclaré de la liaison `name` dans le module `module` à `type`. Renvoie une erreur si la liaison a déjà un type qui n'est pas équivalent à `type`. Si l'argument `type` est absent, définit le type de la liaison sur `Any` s'il n'est pas défini, mais ne renvoie pas d'erreur.

!!! compat "Julia 1.9"
    Cette fonction nécessite Julia 1.9 ou une version ultérieure.

