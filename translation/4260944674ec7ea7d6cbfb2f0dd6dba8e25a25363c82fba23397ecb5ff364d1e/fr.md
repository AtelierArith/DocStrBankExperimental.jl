```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

Trouvez une base de fusion (un ancêtre commun) entre les commits `one` et `two`. `one` et `two` peuvent être tous deux sous forme de chaîne. Retournez le `GitHash` de la base de fusion.
