```
ErrorException(msg)
```

Type d'erreur générique. Le message d'erreur, dans le champ `.msg`, peut fournir des détails plus spécifiques.

# Exemples

```jldoctest
julia> ex = ErrorException("J'ai fait une mauvaise chose");

julia> ex.msg
"J'ai fait une mauvaise chose"
```
