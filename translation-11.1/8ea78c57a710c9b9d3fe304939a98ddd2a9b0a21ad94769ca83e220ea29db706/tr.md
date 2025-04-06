```
LibGit2.split_cfg_entry(ce::LibGit2.ConfigEntry) -> Tuple{String,String,String,String}
```

`ConfigEntry`'yi aşağıdaki parçalara ayırır: bölüm, alt bölüm, ad ve değer.

# Örnekler

Aşağıdaki git yapılandırma dosyasını göz önünde bulundurun:

```
[credential "https://example.com"]
    username = me
```

`ConfigEntry` aşağıdaki gibi görünecektir:

```julia-repl
julia> entry
ConfigEntry("credential.https://example.com.username", "me")

julia> LibGit2.split_cfg_entry(entry)
("credential", "https://example.com", "username", "me")
```

Daha fazla bilgi için [git config sözdizimi belgelerine](https://git-scm.com/docs/git-config#_syntax) bakın.
