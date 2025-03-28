```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

Descompone el `ConfigEntry` en las siguientes partes: sección, subsección, nombre y valor.

# Ejemplos

Dada la configuración de git que contiene:

```
[credential "https://example.com"]
    username = me
```

El `ConfigEntry` se vería así:

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

Consulta la [documentación de sintaxis de git config](https://git-scm.com/docs/git-config#_syntax) para más detalles.
