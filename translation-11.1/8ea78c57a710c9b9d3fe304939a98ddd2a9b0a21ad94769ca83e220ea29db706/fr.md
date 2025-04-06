```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

Décomposez le `ConfigEntry` en les éléments suivants : section, sous-section, nom et valeur.

# Exemples

Étant donné le fichier de configuration git contenant :

```
[credential "https://example.com"]
    username = me
```

Le `ConfigEntry` ressemblerait à ceci :

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

Consultez la [documentation de la syntaxe de la configuration git](https://git-scm.com/docs/git-config#_syntax) pour plus de détails. ```
