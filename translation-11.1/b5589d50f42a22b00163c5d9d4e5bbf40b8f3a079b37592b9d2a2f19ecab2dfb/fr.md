```
dlsym(handle, sym; throw_error::Bool = true)
```

Recherchez un symbole à partir d'un handle de bibliothèque partagée, renvoyez un pointeur de fonction appelable en cas de succès.

Si le symbole ne peut pas être trouvé, cette méthode lève une erreur, sauf si l'argument clé `throw_error` est défini sur `false`, auquel cas cette méthode renvoie `nothing`.
