```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

Imprime `msg` comme un avertissement de dépréciation. Le symbole `funcsym` doit être le nom de la fonction appelante, qui est utilisé pour s'assurer que l'avertissement de dépréciation n'est imprimé qu'une seule fois pour chaque lieu d'appel. Définissez `force=true` pour forcer l'avertissement à toujours être affiché, même si Julia a été démarré avec `--depwarn=no` (par défaut).

Voir aussi [`@deprecate`](@ref).

# Exemples

```julia
function deprecated_func()
    Base.depwarn("N'utilisez pas `deprecated_func()` !", :deprecated_func)

    1 + 1
end
```
