```
devnull
```

Utilisé dans une redirection de flux pour supprimer toutes les données qui y sont écrites. Essentiellement équivalent à `/dev/null` sur Unix ou `NUL` sur Windows. Utilisation :

```julia
run(pipeline(`cat test.txt`, devnull))
```
