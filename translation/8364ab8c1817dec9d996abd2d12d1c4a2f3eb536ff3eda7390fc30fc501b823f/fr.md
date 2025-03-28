```
fdio([name::AbstractString, ]fd::Integer[, own::Bool=false]) -> IOStream
```

Crée un objet [`IOStream`](@ref) à partir d'un descripteur de fichier entier. Si `own` est `true`, la fermeture de cet objet fermera le descripteur sous-jacent. Par défaut, un `IOStream` est fermé lorsqu'il est collecté par le ramasse-miettes. `name` vous permet d'associer le descripteur à un fichier nommé.
