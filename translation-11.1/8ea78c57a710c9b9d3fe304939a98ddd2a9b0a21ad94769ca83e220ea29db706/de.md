```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

Zerlege den `ConfigEntry` in die folgenden Teile: Abschnitt, Unterabschnitt, Name und Wert.

# Beispiele

Gegeben ist die Git-Konfigurationsdatei, die Folgendes enthält:

```
[credential "https://example.com"]
    username = me
```

Der `ConfigEntry` würde wie folgt aussehen:

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

Siehe die [Git-Konfigurationssyntax-Dokumentation](https://git-scm.com/docs/git-config#_syntax) für weitere Details. ```
