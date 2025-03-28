```
homedir() -> String
```

Renvoie le répertoire personnel de l'utilisateur actuel.

!!! note
    `homedir` détermine le répertoire personnel via `libuv`'s `uv_os_homedir`. Pour plus de détails (par exemple sur la façon de spécifier le répertoire personnel via des variables d'environnement), voir la [documentation de `uv_os_homedir`](http://docs.libuv.org/en/v1.x/misc.html#c.uv_os_homedir).


Voir aussi [`Sys.username`](@ref).
